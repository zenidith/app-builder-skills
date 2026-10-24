# Frederick James: "How I'd speed run my app to $13k/m (again)"

Source: a post on X by Frederick James (@frederickjames). The post date was not checked.
This is a paraphrased summary, not a copy of the post. His profile showed $3,922 a month and
$6,259 in revenue at the time it was shared; those are his own claims, not checked.

## 1. The app

- Pick an unsaturated niche, or a new idea. Spend about a week finding it: ideas, thinking,
  research. Building yet another calorie app and expecting sales is the classic mistake.
- Build for iOS only, in native Swift. The new Liquid Glass look makes good UI easy.
- Browse Pinterest for references and remake the assets. Use as little text as possible.
- Backend on Cloudflare: R2 for images, D1 for the database. Simple infrastructure. He says
  never to use Firebase.
- Pay a designer for App Store screenshots. Good ones exist for about $50, and most founders
  lack the taste to do it well themselves.
- Measure onboarding with PostHog. Aim for 90% completion; under 80% means something is wrong.
- About 12–13 screens in total. The paywall should be clean and minimal.
- Add a transaction-abandon offer in a later release.

## 2. Release day

- Run Apple Search Ads from day one, on competitor keywords. Get as many downloads as possible
  in the first week; it matters for the App Store algorithm later.
- In the right niche, with good positioning, Apple Ads alone can get an app to at least $1k a
  month.
- Do founder-led content on TikTok and Instagram. Friends of his say trial reels work very well.

## 3. Scaling

- Use AppsFlyer or Singular as the MMP (or build your own), then scale with TikTok and Meta ads.
- Shotgun the ads: run as many as possible at first to find a format that works.
- If ads are only just under profitable, keep running them; if profitable, keep them going.
  Judge it by comparing LTV with CPA. (The post writes "LTV < CPA"; the sense is that ads are
  fine while LTV is at or near CPA.)
- Ads take a while to get going and cost about $1k to start. If that feels risky, validate the
  app first with organic content and Apple Ads.

## 4. Loop and iterate

- Keep improving the app and reduce churn as much as possible. A leaky bucket loses free
  renewal money.
- Automate as much as possible. Automating App Store Connect submissions through its API, so
  updates ship on their own, was a game changer for him.
- Keep trying new formats and marketing ideas. This is what worked for him; experiment.

## Closing points

- Positioning and the idea matter most, especially for Apple Ads. They do not work on generic
  app ideas.
- Stay in line with Apple. His upsells were all approved through app updates and mentioned in
  the release notes.
- It takes a lot of effort and consistency. It is simple to list, not simple to do. Do not
  overthink it; keep going.
