---
name: app-launch-playbook
description: Complete checklist from idea validation to App Store submission for indie iOS/iPadOS apps. Use when starting a new app project, validating an app idea before building, planning the MVP feature set, deciding when to ship vs add more features, or preparing for App Store launch. Based on the experimentation loop: build small, test with real users, iterate based on feedback, release free on web before App Store.
---

# App Launch Playbook

A practical framework for taking an app idea from concept to App Store launch, built around the experimentation loop. Based on Adam Lyttle's "Transmutation" approach: test early, test often, ship when it's useful (not when it's perfect).

**Source:** Adam Lyttle, "building apps? you need to hear this," 21 Oct 2026 (https://www.youtube.com/watch?v=FTevkxTWtbY), covering the experimentation loop, web-first releases, and avoiding AI-generated copycat apps.

## Core principle: The Experimentation Loop

Don't build in isolation for months. Instead:

1. **Start with a tiny prototype** — core idea only, minimal features
2. **Test it on friends and family** — get real feedback from real people
3. **Release a free web build** — broader audience, lower friction than App Store
4. **Iterate based on actual usage** — add features people request, not features you guess they want
5. **Submit to App Store** — when the web version proves the concept works

**Why this works [AL 4:03–4:10]:**
- You validate the idea before investing months
- You get feedback when changes are cheap (early prototype) not expensive (after launch)
- You avoid building features nobody asked for
- You have proof of concept before App Store review

**Example [AL 7:17, 15:35–15:38]:** Adam's "Cozy Cat House" game was released for free on the web to gather feedback before App Store submission.

## The playbook

### Phase 1: Idea validation (before writing code)

**1. Source the idea**
- ✓ Comes from your own life (a problem you encountered, a workflow you built, a gap you noticed)
- ✓ OR comes from a proven category where you have a unique angle
- ✗ Avoid: copying other indie hackers' apps without bringing anything new [AL 00:21–01:03]
- ✗ Avoid: AI-generated ideas that match dozens of existing apps

**Why it matters:** People can report copycat apps as fraud, risking your entire Apple developer account [AL 00:54]. Apps from your own experience have inherent differentiation.

**App Store check for AI ideas:**
If an AI suggested this idea, search the App Store for existing apps solving the same problem. If 5+ polished apps dominate with strong ratings, consider whether you have a meaningfully different approach before proceeding.

**2. Write the core value in one sentence**
- Who is this for?
- What problem does it solve?
- Why would they come back?

Example: "Pet owners who forget to give medication → daily reminders with dose tracking → peace of mind their pet gets the right care."

**3. Validate keywords (ASO check)**
- Search App Store for the top 3 keywords your idea targets
- Check competition: how many apps rank for those terms?
- Check quality: are they actively maintained, well-reviewed?
- Decision: If keywords are dominated by established apps, you need a unique angle or better execution

### Phase 2: Build the tiny prototype

**4. Define the MVP (minimum viable product)**
- Strip the idea to its **core mechanic** — the one thing it must do well
- Cut every feature that isn't essential to proving the concept
- Aim for "useful in one scenario" not "complete"

**Example:** Medication reminder app MVP:
- ✓ Add one medication
- ✓ Set a daily reminder time
- ✓ Mark as taken
- ✗ Multiple pets (add later)
- ✗ Refill tracking (add later)
- ✗ Vet appointment sync (add later)

**5. Build the prototype**
- Focus on functionality, not polish
- UI can be rough (you'll iterate)
- No marketing site, no fancy onboarding yet
- Goal: something a friend can actually use

**Time budget:** Days to 2 weeks, not months.

### Phase 3: Test with friends and family

**6. Distribute via TestFlight or web**
- TestFlight: up to 10,000 external testers, but requires Apple review for external testing
- Web (for cross-platform apps): deploy a free web version (faster, no review)
- Ask 5–10 people to use it for real tasks, not just "look at it"

**7. Gather feedback**
- What's confusing?
- What's missing that would make it actually useful?
- What features did they expect that aren't there?
- What did they try to do that didn't work?

**8. Iterate on the core**
- Fix broken flows
- Clarify confusing UI
- Add **only** the features people specifically requested
- Resist adding features you think are clever but nobody asked for

**Rule [AL 02:11–02:27]:** Ship what you have. Start getting real usage now. Build features when users request them, not preemptively.

### Phase 4: Free web build (optional but recommended)

**9. Release on the web before App Store [AL 15:35–18:35]**
- Deploy a free web version (if your app works on web)
- Share it publicly (social media, forums, communities)
- Easier distribution than App Store (no review wait)
- Broader testing audience
- Prove the concept gets traction

**10. Monitor web usage**
- Are people using it?
- Are they coming back?
- What features are they requesting?
- Is there organic sharing/word-of-mouth?

**Decision point:** If the web version gets no traction, adding App Store distribution won't fix it. Either the idea needs iteration or it's not solving a real problem.

### Phase 5: Prepare for App Store

**11. Polish the UX**
- Now that the core works, invest in polish
- Smooth onboarding
- Clear empty states
- Helpful error messages
- App Store screenshots that show the value (not just pretty UI)

**12. Write App Store copy**
- App name: clear, searchable (not clever/obscure)
- Subtitle: describes what it does in <30 chars
- Description: leads with the problem it solves, not a feature list
- Keywords: based on actual App Store search, not guesses (use App Store Connect's keyword tool)

**13. Set pricing strategy**
- Don't blindly copy "$70 lifetime" [AL 01:43–02:05]
- Test different models:
  - Free with IAP (in-app purchase)
  - Paid up-front
  - Subscription (for ongoing value/content)
  - Freemium (free tier + premium)
- Experiment with localized pricing (different prices per country)

**14. Screenshots and assets**
- 6.5" iPhone screenshots (required)
- 12.9" iPad Pro screenshots (if targeting iPad)
- Optional: App Store header video (21:9 loop, see `appstore-header-loop` skill)
- App icon: 1024x1024, no alpha channel
- Privacy manifest (required since iOS 17)

**15. App Store Connect setup**
- App name, bundle ID, SKU
- Age rating (honest, or risk rejection)
- App privacy details (every data type you collect)
- Support URL (can be a simple site or email link)
- Marketing URL (optional)

### Phase 6: Submit and launch

**16. TestFlight beta (recommended)**
- Submit for TestFlight review first (faster, lower stakes than App Store review)
- Invite a larger group (100–1000 testers)
- Fix any crashes or critical bugs
- Iterate on feedback

**17. Submit for App Store review**
- Export the build
- Upload via Xcode or Transporter
- Add what's new / release notes
- Submit for review

**Review times:** Typically 24–48 hours, sometimes up to 7 days.

**Common rejection reasons:**
- Broken functionality (crashes, unresponsive buttons)
- Misleading screenshots or description
- Privacy manifest errors
- Age rating mismatch
- Spam or low-quality content

**If rejected:** Read the rejection reason carefully, fix the specific issue, re-submit. Don't argue unless the rejection is clearly an error.

**18. Launch**
- Release the app
- Share on social media, Product Hunt, indie communities
- Email anyone who tested the beta
- Ask early users for reviews (but don't incentivize them — that's against guidelines)

### Phase 7: Post-launch

**19. Active marketing (don't rely on ASO alone)**
- ASO (App Store Optimization) is passive — it works, but slowly [AL 02:42–02:56]
- Combine with active outreach:
  - Social media posts
  - Community engagement (Reddit, forums, Discord)
  - Email outreach to relevant blogs/newsletters
  - Content creation (blog posts, videos, tutorials)
  - Direct user acquisition

**Rule:** If a marketing channel isn't bringing measurable users after a fair test (2–4 weeks), stop it and try something else.

**20. Ship updates when users ask**
- User-requested feature > your clever idea [AL 02:32–02:42]
- Fix bugs immediately
- Add features based on actual requests, not preemptive guesses
- Performance improvements users notice

**21. Track profit, not just revenue**
- Monthly profit = what's left after App Store fees (15–30%), subscription services, server costs, tools
- MRR (monthly recurring revenue) means nothing if costs eat it [AL 01:14–01:30]
- Optimize for profit, not vanity metrics

**22. Protect your developer account**
- Remove low-performing apps that aren't worth the risk [AL 03:14–03:22]
- Delete obvious copycats (yes, even if they make a little money)
- Clean up anything that could be flagged: unauthorized content, trademark issues, spam
- Losing one $200/month app is better than losing your whole account with 5+ apps

## Summary: The loop

```
Idea → Tiny prototype → Friends/family test → Iterate → Free web build → 
Gather feedback → Iterate → App Store submission → Launch → Active marketing → 
User-requested updates → Repeat for next app
```

**Key principles:**
- Test early, test often
- Ship when it's useful, not when it's perfect
- Build features users request, not features you guess they want
- Validate on the web before App Store (if possible)
- Marketing is active work, not passive waiting
- Profit matters more than revenue

**Credit:** Adam Lyttle's experimentation loop and anti-copycat principles.

## References

- Adam Lyttle, "building apps? you need to hear this," 21 Oct 2026: https://www.youtube.com/watch?v=FTevkxTWtbY
- Apple App Store Connect Help: https://developer.apple.com/help/app-store-connect/
- App Store Review Guidelines: https://developer.apple.com/app-store/review/guidelines/
- App Store Optimization (ASO) keywords: use App Store Connect's search term reporting
