---
name: appstore-header-loop
description: Create a looping video header and search result asset for an App Store product page. Use when preparing creative assets for an iOS/iPadOS app launch or update, making a promotional header that loops seamlessly, designing App Store search result visuals, or automating header generation for multiple apps. Works for any app with visual brand elements (illustrations, photos, product shots) that can move in a carousel or animation.
---

# App Store Header Loop

How to build a seamless looping video header and static poster for App Store product pages and search results, using code. Based on a production build for a baby-food app with illustrated food items, cream background, drifting pastel blobs, and animated category labels.

## When to use this

Apple allows **21:9 video headers** (3840x1646, 30 or 60 fps, 5–30 s loop) and **3:2 search result videos** (1920x1280 to 3840x2560) on App Store product pages for iOS 27+ and iPadOS 27+. Both loop continuously and play muted by default.

Use this method when:
- Your app has a set of visual items (food, icons, characters, products, features) that can cycle through
- You want a code-based build so you can regenerate it when the brand changes
- The header needs to work silently (no voiceover, no dialogue)
- You need a seamless loop where frame 0 flows into frame N with no visible cut

**Don't use this for:**
- Live-action video (use real footage + editing software instead)
- One static image (export a PNG, done)
- Apps with no visual brand elements to animate

## What you'll need

**Tools:**
- Python 3 with Pillow (PIL)
- ffmpeg (for video encoding and inspection)
- Optional: psd_tools (if you're reading Apple's PSD templates for safe areas)

**Brand assets:**
- App icon, name, and screenshots (from App Store lookup or your repo)
- Visual items to cycle through (illustrations, photos, product shots) — at least 3, ideally 5–8
- Brand colors, fonts, and any category labels or pill text
- Design guidelines (if your app has a design system)

**Specs** (from Apple, Oct 2024):
- Product page **header video**: 21:9, 3840x1646, 30 or 60 fps, 5–30 s, .mov/.m4v/.mp4
- Product page **header image**: 3840x1646, .jpeg/.jpg/.png, no alpha
- Search results **video**: 3:2, 1920x1280 to 3840x2560, 30 or 60 fps, 5–30 s
- Search results **image**: 3:2, 1920x1280 to 3840x2560, .jpeg/.jpg/.png, no alpha
- **Art Safe Area** for header: x 1097 to 2743, y 493 to 1154 (1646x661 px, centred)
- **Art Safe Area** for search: x 836 to 3004, y 765 to 1795 (2168x1030 px)

All text, logos, and key elements must fit inside the safe area. Side elements (decorative blobs, carousel overhang) can extend past it.

**References:**
- Apple's spec page: https://developer.apple.com/help/app-store-connect/reference/app-information/creative-assets-specifications
- Best practices: https://developer.apple.com/app-store/asset-best-practices/
- Templates (PSD, safe areas): https://developer.apple.com/app-store/creative-assets-templates/

## Step-by-step build

### 1. Get the specs and safe areas

Download Apple's header and search PSD templates (links above). Open them in Python with `psd_tools` and read the "Art Safe Area" layer bounds:

```python
from psd_tools import PSDImage

psd = PSDImage.open("header_template.psd")
for layer in psd.descendants():
    if "Art Safe Area" in layer.name:
        print(f"{layer.name}: {layer.bbox}")  # (left, top, right, bottom)
```

Delete the PSDs after (40–100 MB each). The safe areas are:
- Header 3840x1646: x 1097–2743, y 493–1154
- Search 3840x2560: x 836–3004, y 765–1795

### 2. Gather brand assets

**From App Store (if the app is already live):**
```python
import requests
lookup = requests.get(f"https://itunes.apple.com/lookup?id={app_id}").json()
name = lookup['results'][0]['trackName']
icon_url = lookup['results'][0]['artworkUrl512']
screenshots = lookup['results'][0]['screenshotUrls']
# Change /320x480bb.jpg to /645x1398bb.png for bigger screenshots
```

**From your repo:**
- Design guidelines (colors, fonts): `design_guidelines.json` or equivalent
- Visual items: `assets/images/items/*.webp` or `*.png`
- Category labels: `content/items.json` or wherever your data lives

### 3. Configure the loop

Write a `config.json` with:
- Paths to visual items (in carousel order)
- Category label and pill text for each item
- Tint color per item (optional)
- Background color, blob colors, timing
- Poster offset (see Gotchas below)

Example structure:
```json
{
  "items": [
    {"path": "assets/avocado.webp", "label": "fruit", "pill": "soft wedges", "tint": "#A8D5BA"},
    {"path": "assets/sweet-potato.webp", "label": "vegetables", "pill": "steamed", "tint": "#F4A460"}
  ],
  "background": "#FAF3EB",
  "blob_colors": ["#FFE4E1", "#E6F3FF", "#FFF5E1"],
  "duration": 12.0,
  "fps": 30,
  "poster_offset": 6.0
}
```

### 4. Render frames and encode

**The render script** (`build_header.py` or similar):
- For each frame t in [0, fps*duration), draw:
  - Background color
  - Drifting blobs (draw at 1/8 resolution, blur, upscale for speed)
  - Carousel of items, offset by `(t / duration) * item_count`, wrapping
  - White circle at center
  - Category label, pill, and tick for the current item
- Pure functions of t, period duration: `carousel_offset(t) = (t / T) * N % N`
- Render frames 0 to fps*T-1, **never frame T** (or the seam frame plays twice)
- Pipe frames to ffmpeg stdin (no temp files):

```python
ffmpeg_cmd = [
    "ffmpeg", "-y", "-f", "rawvideo", "-pix_fmt", "rgb24",
    "-s", "3840x1646", "-r", str(fps),
    "-i", "pipe:0",  # frames from stdin
    "-c:v", "libx264", "-preset", "medium", "-crf", "16",
    "-pix_fmt", "yuv420p", "-level", "5.1",
    "-color_primaries", "bt709", "-color_trc", "bt709", "-colorspace", "bt709",
    "-movflags", "+faststart", "-an",  # no audio
    "-g", str(fps),  # GOP = fps
    output_path
]
proc = subprocess.Popen(ffmpeg_cmd, stdin=subprocess.PIPE)
for t_frame in range(int(fps * duration)):
    frame_pil = render_frame(t_frame / fps, config)
    proc.stdin.write(frame_pil.tobytes())
proc.stdin.close()
proc.wait()
```

**Poster frame:**
```bash
python3 build_header.py frame 0 poster.png
```

**Header video (21:9, 3840x1646):**
```bash
python3 build_header.py video header.mp4 30
```

**Search result video (3:2, but 3840x2560 exceeds H.264 Level 5.1 frame size, so render at 2880x1920):**
```bash
python3 build_header.py video search.mp4 30 search
```
Add `-vf scale=2880:1920` in the ffmpeg command for the search asset.

**Search result image (3:2, 3840x2560):**
```bash
python3 build_header.py frame 0 search.png search
```

Rendering takes about 1 min per 12 s video on 4 CPUs.

### 5. Inspect and verify

**Check the loop seam:**
```bash
# Extract frames 0, middle, last
ffmpeg -i header.mp4 -vf "select=eq(n\,0)" -frames:v 1 frame_0.png
ffmpeg -i header.mp4 -vf "select=eq(n\,179)" -frames:v 1 frame_mid.png
ffmpeg -i header.mp4 -vf "select=eq(n\,359)" -frames:v 1 frame_last.png
```

Compare frame 359 → 0 vs frame 0 → 1 (mean absolute difference in Python/PIL). They should be nearly identical (e.g. 0.10 vs 0.10).

**Check specs:**
```bash
ffprobe header.mp4
```
- Duration: exactly 12.000 s
- Frame count: 360 (= 30 fps × 12 s)
- Codec: H.264 High, Level 5.1
- Pixel format: yuv420p
- Color space: BT.709
- No audio track

**Check safe area:** Open the poster PNG in your image editor, overlay the safe area box, and confirm all text and the center circle fit inside.

**Check poster = frame 0:** The poster PNG should be pixel-identical to frame 0 of the video.

## Gotchas (from production)

### Seamless loop
Make every motion a **pure function of t with period T**. The carousel advances exactly one item per loop (`p(T) = N`), which wraps to 0. Blob drift and bobbing use `sin(2π t / T)` or `cos(2π t / T)` with period T or T/2.

**Render frames 0 to fps*T-1, never frame T**, or the seam frame plays twice.

### Poster frame = frame 0
Offset the timeline so t=0 lands in the **middle of a rest**, with labels and tick fully visible, not mid-motion. Use a `poster_offset` in config and render the video starting at `t = poster_offset % duration`.

### Tick flicker
First version faded the tick in as the food arrived, then reset it to 0 to "pop" it. That gave a one-frame blink. Fix: only the **leaving** item's tick shrinks, and the **arriving** one pops after it lands.

### Safe area is small
1646x661 px of 3840x1646. All text and the centre circle must fit. Text under ~48 px at 3840 wide gets tiny on a phone.

### Encoding
- H.264 High, `-level 5.1`, yuv420p, BT.709 color tags, `-movflags +faststart`, `-an` (no audio), CRF 16, GOP = fps
- 3840x2560 H.264 exceeds Level 5.1/5.2 frame size, so the 3:2 search video renders at 2880x1920 (`-vf scale=2880:1920`)

### Background blobs
Draw them at **1/8 resolution**, blur, then upscale. Fast and blurry art upscales cleanly. Size blobs from the 21:9 height, or a 3:2 canvas gets muddy-grey blobs.

### Small source art
256 px illustrations are fine up to ~1.4x in the header. The 3:2 search asset uses 2.3x, which is acceptable at display size but not crisp.

### Process
When running a long render in a notebook, start it with `Popen` (log to file, `start_new_session=True`). Never capture the output of a long ffmpeg pipe with `subprocess.run(..., capture_output=True)` — it holds the turn for hours.

## Example config snippet

```json
{
  "items": [
    {
      "path": "assets/foods/avocado.webp",
      "label": "fruit",
      "pill": "soft wedges",
      "tint": "#A8D5BA"
    },
    {
      "path": "assets/foods/egg.webp",
      "label": "allergen",
      "pill": "well-cooked strips",
      "tint": "#FFE4B5"
    }
  ],
  "background": "#FAF3EB",
  "blob_colors": ["#FFE4E1", "#E6F3FF", "#FFF5E1", "#F0E6FF"],
  "circle_color": "#FFFFFF",
  "text_color": "#2C2C2C",
  "tick_color": "#4CAF50",
  "duration": 12.0,
  "fps": 30,
  "poster_offset": 6.0
}
```

## What to avoid

- **Don't reveal the app name in the skill text** if you're generalizing it. Describe it as "a baby-food app with illustrated foods" or similar.
- **Don't invent claims.** If the generator script checks "prep method is safe for babies," that's a product decision, not a visual one. Keep the skill focused on the creative asset build.
- **Don't upload anything to App Store Connect without the owner's yes.**

## Verification checklist

Before sharing the assets:
- [ ] Loop seam is invisible (frame 359 → 0 matches frame 0 → 1)
- [ ] Poster is pixel-identical to frame 0
- [ ] All text and key elements fit inside the safe area
- [ ] No flicker (tick, labels, items all move smoothly)
- [ ] PNGs are RGB, no alpha
- [ ] Videos: H.264 High@5.1, yuv420p, BT.709, no audio, faststart flag
- [ ] Duration and frame count match specs
- [ ] File sizes under any known limits (none stated by Apple for video; posters under ~1 MB is safe)

## References

- **Apple specs:** https://developer.apple.com/help/app-store-connect/reference/app-information/creative-assets-specifications
- **Best practices:** https://developer.apple.com/app-store/asset-best-practices/ (keep key art in safe area, choose strong poster frame, loop seamlessly, avoid quick cuts, work silently, no prices/URLs/awards/badges, 4+ rating)
- **Templates:** https://developer.apple.com/app-store/creative-assets-templates/ (PSD files with safe area layers)
- **Announcement:** https://developer.apple.com/news/?id=ljpl7kyn (Oct 5, 2026)
