---
name: app-marketing-website
description: Build a website for your iOS/Android app to improve discoverability through search engines and AI recommendations (ChatGPT, Claude, Gemini). Use when launching a new app, improving an existing app's reach, building SEO presence for an underserved niche, setting up for AI crawler recommendations, planning content strategy, or managing a portfolio of apps. Most useful for indie apps in niches where competitors don't have websites.
---

# App marketing through websites

Why most app founders skip building a website, why that's a mistake in 2026, and what to build. Based on tested results from an indie maker managing multiple apps.

Source: Dan Kulkov, "simply STUPID marketing tactic to grow your ios app", 19 Oct 2026 (https://www.youtube.com/watch?v=feHmwvbNwvc)

## The opportunity [00:14]

**The pattern:** Most app founders never build a website. They think the App Store page is enough.

**Why it's wrong in 2026:**
1. **Search engines can't deeply index App Store pages** — your app is invisible to Google for most searches [00:24]
2. **ChatGPT/Claude need websites to recommend your app** [00:35] — AI models scrape and recommend based on web content, not App Store listings
3. **Underserved niches** — If competitors don't have websites, you win by default [00:48]

**Speaker's claim (unverified) [00:42]:** "In underserved niches, adding a website helped my apps rank higher in both search and AI recommendations within weeks."

## Why it works in underserved niches [00:48]

In crowded markets (meditation, habit tracking), every app has a polished website, so adding yours is table stakes. But in **underserved niches** — micro-tools, specific workflows, niche utilities — most apps have NO website at all.

**The leverage:** You're competing against App Store pages, not real websites. A simple, well-structured site beats no site every time.

## Recommended tech stack: Astro [01:02]

**Why Astro [01:06]:**
- **Lightning fast** — static HTML, minimal JS
- **Multi-app management** — Easy to manage 5-10 app sites in one repo if you have a portfolio
- **Free hosting** — Netlify, Vercel, Cloudflare Pages
- **Template reuse** — Build the structure once, replicate per app

Alternative: Next.js, Hugo, Eleventy, or even a Carrd/Webflow nocode site. The tech matters less than having **something**.

## Core site structure [01:18]

Keep it simple. 5-7 pages covers 90% of needs:

1. **Homepage**
   - What the app is (one clear sentence)
   - Who it's for
   - Primary CTA (App Store badge)
   - Screenshot or demo

2. **How it works** [01:24]
   - Step-by-step walkthrough
   - Screenshots for each step
   - Address common "can it do X?" questions

3. **Features page** [01:31]
   - Bullet list of features
   - Keyword-rich (the words users search)
   - Each feature explained in plain terms

4. **Audience segments** [01:38]
   - E.g., "For students", "For freelancers", "For parents"
   - Separate page or sections
   - Helps search and AI understand WHO it serves

5. **Testimonials/reviews** [01:44]
   - Pull real App Store reviews
   - Quotes from users (with permission)
   - Social proof builds trust

6. **Blog** (optional but powerful for SEO)
   - Keyword-targeted guides
   - Listicles ("best X apps in 2026", "Y alternatives")
   - Educational content

## Localization [01:52]

**Rule:** If your app is localized, your website should be too.

**Why:** Each language creates a separate set of keywords, backlinks, and AI training data. A Japanese app with only an English site misses the entire Japanese search audience.

**Implementation in Astro:** Use its i18n routing (`/`, `/ja`, `/es`, etc.). Each localized page gets its own URL, sitemap entry, and can rank independently.

## App Store integration [02:03]

**Critical step most skip [02:08]:** Add your website URL to the App Store **Marketing URL** field (in App Store Connect).

**Why it matters:**
1. Apple shows it on your App Store page
2. Creates a backlink (App Store → your site)
3. If localized, each locale's App Store page links to the matching site version
4. Signals to Apple and search engines that your app is legitimate

## Content strategy [02:18]

Three content types, ranked by effort and impact:

### 1. Keyword-targeted guides [02:24]

**The formula:** Pick 20 keywords related to your app's niche. Write one guide per keyword over 14 days.

**Speaker's claim (unverified) [02:30]:** "I published 20 keyword guides over 14 days and saw search traffic within a week."

**Example keywords** (for a Japan travel app):
- "how to use JR pass"
- "japan itinerary 7 days"
- "best time to visit tokyo"

Each guide links back to the app as the solution.

### 2. Free tools and calculators [02:42]

**Why they work:**
- People link to tools (natural backlinks)
- Highly shareable
- Ranks well for "X calculator" or "X tool" searches
- Positions your app as the full solution

**Examples:**
- Currency converter (for a finance app)
- Calorie calculator (for a diet app)
- Trip cost estimator (for a travel app)

**Build once, earn links forever.**

### 3. Listicles [02:56]

Two formats:

**A) "Best [niche] apps in 2026"**
- Includes your app + 5-10 competitors
- Rank your app #1 or #2 (be honest about features)
- Users searching "best X app" find this
- You control the narrative

**B) "[Competitor] alternatives"**
- Target users already searching for competitors
- "Looking for a [BigApp] alternative? Here are 7 options"
- Include your app as one option
- Captures intent-rich traffic

**Ethics:** Be fair. Don't trash competitors. Focus on what makes each app (including yours) unique.

### 4. Educational content [03:12]

Least useful for direct conversions, but builds authority:
- "How to [solve problem your app solves]"
- Industry trends
- Beginner guides

**Trade-off:** Takes time, less direct ROI than keyword guides or tools.

## Multi-app portfolio strategy [03:24]

**The reusable skill [03:28]:** If you have 5 apps, build the website structure once (HTML, CSS, Astro template), then replicate it per app with swapped content.

**Checklist per app:**
- Swap logo, colors, app name
- Rewrite homepage/features for this app's niche
- Adjust keywords
- Keep the same pages (how it works, features, testimonials)

**Time saved:** First site takes 2-3 days. Each additional site takes 4-6 hours.

## AI agent SEO integration [03:42]

**Optional for power users:** Give an AI agent (Claude, ChatGPT via API, or a custom assistant) access to:
- Google Search Console data (impressions, clicks, position)
- Keyword research tools (Ahrefs, SEMrush, or free alternatives)
- Your content calendar

**What it does:**
- Checks which pages rank positions 5-15 (high impressions, low clicks)
- Suggests title/meta tweaks to improve CTR
- Identifies new keywords to target

**Speaker's setup (unverified):** Uses an AI agent to review GSC data weekly and suggest quick wins.

## AI crawler optimization [04:02]

ChatGPT, Claude (via Claude.ai search), and Gemini all crawl the web to train and answer queries. Make your site friendly to them:

1. **Structured data** (JSON-LD schema)
   - Use `SoftwareApplication` schema for the app
   - Include name, description, operatingSystem, offers (price)

2. **Clear headings and lists**
   - AI models extract from `<h2>`, `<ul>`, `<table>`
   - Avoid walls of text

3. **robots.txt**
   - Allow all crawlers (default)
   - Block only admin/test pages

4. **Sitemap** (XML)
   - Submit to Google, Bing
   - AI models may follow sitemap links

5. **Fast site** (under 2s load)
   - AI crawlers penalize slow sites in training data

## Summary

| Action | Impact | Effort |
|---|---|---|
| Build a basic 5-page site | High in underserved niches | 2-3 days first time |
| Add website URL to App Store | Medium (backlink + legitimacy) | 5 minutes |
| Localize site if app is localized | High for non-English markets | +1-2 days per language |
| Publish 20 keyword guides | High for SEO, medium for AI | 14 days (1-2 per day) |
| Build 1-2 free tools | Medium-high (backlinks) | 1-2 days per tool |
| Publish "best [niche] in 2026" listicle | Medium (intent-rich traffic) | 3-4 hours |
| Publish "[competitor] alternatives" | Medium (captures competitor searches) | 3-4 hours |
| Set up for AI crawlers (schema, fast site) | Medium (future-proofing) | 4-6 hours |

## When to skip this

- **Crowded market with strong competitors:** If all competitors have polished websites, yours needs to be equally good or better. A half-done site won't beat them. In that case, content quality matters more than just "having a site."
- **Pure utility with no search intent:** If users only find your app through App Store browse or word of mouth (e.g., a hyper-niche internal tool), a website may not move the needle.
- **No bandwidth:** If you're choosing between shipping app features users asked for vs building a site, ship features first. Website comes after product-market fit.

## Tools mentioned

**Free web app tools (activationpal.com/tools):**
1. **App revenue calculator** — Project 12-month revenue from installs, conversion, and pricing
2. **Funnel calculator** — Conversion rates through onboarding steps
3. **ARPU calculator** — Average revenue per user
4. **Cohort analysis tool** — Retention heatmap
5. **App Store account audit** — Portfolio review for risks
6. **ASO tools directory** — 54 ASO tools with prices

All free, web-based calculators. The main ActivationPal product (analytics) is paid, but these tools are free.

**Recommendation:** The **App revenue calculator** is useful for projecting impact of pricing experiments (see **app-building-mindset** skill). The **funnel calculator** helps diagnose where onboarding drops off.

## Sources and claims

- All timestamps reference: https://www.youtube.com/watch?v=feHmwvbNwvc
- **Unverified speaker claim [00:42]:** "Website helped rank in weeks in underserved niches"
- **Unverified speaker claim [02:30]:** "20 guides in 14 days, traffic in a week"
- **Unverified speaker claim [03:42]:** AI agent SEO setup — described but not independently verified
- Tool URLs verified as of 2026-10-22: activationpal.com/tools has 6 free calculators (account audit, revenue, funnel, ARPU, cohort, ASO tools)

## Related

- **app-building-mindset** — Avoid common app-building mistakes (pricing experiments, marketing vs features, securing your developer account)
- **SEO for SaaS** (not a skill yet) — More advanced SEO tactics (link building, technical SEO, local SEO)
- **ASO fundamentals** (not a skill yet) — App Store Optimization as complement to website strategy
