---
name: app-launch-playbook
description: Plan, launch and grow an indie iOS app from idea to steady subscription revenue, as a phase-by-phase checklist. Use when picking an app idea or niche, checking whether an app idea is too generic, planning an iOS app build (native Swift, simple backend, onboarding, paywall), preparing App Store screenshots, setting onboarding and paywall targets, planning launch week, setting up Apple Search Ads on competitor keywords, planning founder-led TikTok or Instagram content, deciding when to start paid TikTok or Meta ads, choosing a measurement partner (MMP), judging ads with LTV vs CPA, cutting churn, or automating App Store Connect submissions. Use it even if the user just says "how do I launch this app?", "why is nobody downloading my app?", "should I run ads yet?", "is this app idea any good?" or shares an app and asks what to do next.
---

# App launch playbook

A four-phase checklist for taking one indie iOS app from idea to paid growth: idea and niche,
build, launch, then scale and loop. Run it once per app. Tick items off, write the real numbers
next to them, and come back to phase 4 every few weeks.

It is based on one founder's public post (see Credit). His numbers are his own claims and are
marked **[FJ]**. Everything else is this skill's working default; change it if your data disagrees.

| Need | Read |
|---|---|
| A summary of the original post, point by point | `references/frederick-james-post-notes.md` |
| A blank per-app checklist to copy and fill in | `templates/app-launch-checklist.md` |
| Picking and scoring the niche itself | `../niche-selection/SKILL.md` |
| Writing the App Store name, subtitle, screenshots copy and paywall copy | `../copywriting/SKILL.md` |

## Ground rules

- Positioning and the idea matter most. Apple Ads do not work on generic ideas. [FJ]
- Do not build a "me too" app. A plain calorie counter in a crowded chart will not sell. [FJ]
- Numbers are real or marked. Write the source and date next to every figure; mark guesses
  `[estimate]`.
- Stay inside Apple's rules. Every upsell and offer ships in an app update that goes through
  review, and is described in the release notes. [FJ]
- Nothing is spent, submitted or published without the owner's yes.
- It takes a lot of effort and consistency. Do not overthink it; keep shipping. [FJ]

## Phase 1: Idea and niche

Goal: one idea in an unsaturated niche, or a genuinely new idea, with clear positioning.

- [ ] Block out a research week. Brainstorm, look at charts and reviews, read competitors. [FJ]
- [ ] Run the candidates through the `niche-selection` skill. Compare several side by side.
- [ ] Check saturation: who ranks for the main keywords, how many reviews do the top 5 have,
      how recently did they update?
- [ ] Write the positioning in one line: who it is for, the one job it does, why it beats the
      generic option. If you cannot, the idea is too generic.
- [ ] List 10–20 competitor app names and keywords. You will bid on these at launch.
- [ ] Decide: go, or back to the list.

### Before you build: the experiment loop

Don't disappear for months building in private. Run the idea through small, cheap tests first:

1. **Tiny prototype.** Only the core idea, nothing else.
2. **Friends and family.** Put it in real hands and watch what they actually do.
3. **Free web build.** Release a simple web version to a wider audience; it is cheaper to change than an App Store build.
4. **App Store.** Submit once people keep using the web version, and add features they ask for, not ones you guess at.

Each step is cheaper to change than the next, so most wrong ideas die early. (Adapted from Adam Lyttle's experimentation loop.)

## Phase 2: Build

Goal: a simple, good-looking native app with an onboarding that converts.

- [ ] iOS only, native Swift and SwiftUI. Use the current system look (Liquid Glass). [FJ]
- [ ] Use as little text as possible on screen. [FJ]
- [ ] Collect visual references (e.g. Pinterest) and remake the assets in your own style. [FJ]
- [ ] Keep the backend simple: Cloudflare R2 for images, Cloudflare D1 for the database. The
      author avoids Firebase. [FJ]
- [ ] Get professional App Store screenshots. Paying a designer (around $50 [FJ]) is often worth it.
- [ ] Add analytics (e.g. PostHog) and track every onboarding step as an event.
- [ ] Onboarding plus paywall: about 12–13 screens in total. [FJ]
- [ ] Target onboarding completion of 80–90%. Below 80%, fix the onboarding before anything else. [FJ]
- [ ] Paywall: clean and minimal. [FJ]
- [ ] Plan a transaction-abandon offer (shown when someone backs out of the purchase) for a
      follow-up release, not the first one. [FJ]
- [ ] Any upsell goes in through an app update and review, noted in the release notes. [FJ]

## Phase 3: Launch

Goal: as many downloads as possible in week 1. Early downloads feed the App Store algorithm. [FJ]

- [ ] Apple Search Ads live from day one. [FJ]
- [ ] Bid on competitor keywords from your phase 1 list. [FJ]
- [ ] Set a daily budget and a total cap before launch, and check results daily.
- [ ] Founder-led content on TikTok and Instagram: you, the problem, the app. [FJ]
- [ ] Try Instagram trial reels (shown to non-followers first) to test hooks cheaply. [FJ]
- [ ] Write down week-1 downloads, trial starts and revenue as your baseline.
- [ ] Expectation: in the right niche with good positioning, Apple Ads alone can carry an app
      to about $1k a month. [FJ]

## Phase 4: Scale and loop

Goal: grow with paid ads while they pay back, and keep the bucket from leaking.

- [ ] Validate first. Only scale once organic and Apple Ads show people pay. [FJ]
- [ ] Set up an MMP (mobile measurement partner) such as AppsFlyer or Singular, or build your
      own attribution. [FJ]
- [ ] Start TikTok and Meta ads. Budget about $1k to get them going; they take a while. [FJ]
- [ ] Shotgun the ads: run many formats and hooks at first, then keep the winners. [FJ]
- [ ] Keep an ad running while LTV is at or above CPA. If it is only just under, keep it going
      while you improve it. Cut ads that are clearly losing. [FJ]
- [ ] Cut churn as much as you can. Every lost subscriber is free renewal money gone. [FJ]
- [ ] Automate App Store Connect submissions through its API, so updates ship without manual
      steps. [FJ]
- [ ] Keep testing new formats and channels. What worked for one app is a starting point. [FJ]
- [ ] Review the metrics table below every 2–4 weeks and pick the weakest number to fix next.

## Metrics to track

Targets marked [FJ] are the author's numbers. Blank targets: set your own from your baseline.

| Metric | What it is | Target |
|---|---|---|
| Onboarding completion % | Users who finish onboarding / users who start it | 80–90% [FJ] |
| Trial start % | Trials started / new installs | No number in the post; set from baseline |
| Trial → paid % | Trials that convert to a paid plan | No number in the post; set from baseline |
| CPA | Ad spend / paying customers acquired | At or below LTV [FJ] |
| LTV | Average revenue per paying customer over their lifetime | At or above CPA [FJ] |
| Churn | Share of subscribers who cancel each period | As low as possible [FJ] |

## Common mistakes

- A generic idea, then blaming the ads.
- Launching with no Apple Ads and waiting for organic downloads.
- A long, wordy onboarding nobody finishes.
- Scaling paid ads before checking anyone pays.
- Upsells added without an app update and review.
- Measuring nothing, so every change is a guess.

## Credit

The experiment loop before Phase 2 is adapted from Adam Lyttle.


Based on a post by Frederick James (@frederickjames on X).
