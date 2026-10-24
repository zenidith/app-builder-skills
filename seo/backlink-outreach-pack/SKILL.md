---
name: backlink-outreach-pack
description: Copy-paste prompt pack and execution framework for white-hat link building, niche edits, NGO donor links, parasite SEO, broken link building, and digital PR. Use when prospecting backlink opportunities, finding verified contacts, and drafting high-converting outreach pitches.
---

# Backlink Outreach Pack

A self-contained library of link-building and digital PR prompts optimized for Codex, Claude Code, Antigravity, and terminal-based research agents.

Prerequisite: Ensure web search is enabled in your agent environment before running these prompts.

### The Agent Split

- The Agent (80%): Live SERP discovery, outbound link validation, 404 response inspection, contextual sentence isolation, and outreach drafting.
- You (20%): Sending personal emails, submitting directory forms, making donations, or registering domains.

---

## Prompt 00 - Ground Rules (Optional Foundation)

Ground rules for everything I ask next:
- Real data only. Every site, URL, email, or price must come from a live page you actually found and inspected this session - include the exact source link. If you can't find or confirm it, write "not found / unconfirmed". Never guess, approximate, or hallucinate.
- Judge quality by verifiable signals: skip dead, abandoned, or spammy sites; favor active sites that clearly index on Google, publish regularly, and maintain natural editorial standards. Never output fabricated domain authority or rating metrics.
- One row per domain. Rank by topical fit and authority. Mark your top 3 picks with a star.
- Contact discovery: extract verified email addresses from the site. If no public direct email is listed, write "form only -> [contact URL]".
- Outreach copy: keep pitches brief, specific, and human. Omit fluff, false praise ("I love your content"), and generic pleasantries.
- Web search status: if web search is unavailable or you cannot inspect an external page, state this immediately instead of providing estimated data.

---

# S TIER

## 1. NGO & Charity Links

Support a non-profit while securing an editorial backlink from a verified donor/sponsor roster.

Prompt to run:
You're my SEO link-building assistant.
Business: [BUSINESS + WHAT YOU DO]
Location: [CITY/REGION, OR "GLOBAL/REMOTE"]
Site: [URL]

Goal: Identify verified nonprofits and charities that maintain public donor or supporter pages with active outbound hyperlinks, where a modest donation earns an official backlink.

Rules:
- Real data only: include direct source links for the donation page and the supporters page.
- Skip directory pages (GreatNonprofits, Charity Navigator, GuideStar, GlobalGiving) and payment processors (GoFundMe, JustGiving, Donorbox, Every.org). Collect the charity's OWN root domain.
- MANDATORY VERIFICATION: Only list a charity if you personally open its supporters/partners page and confirm that donor logos or names contain hyperlinked <a> tags linking off-site. Drop any organization with an unlinked logo wall.
- One row per charity, ranked by topical or local relevance. Star your top 3 recommendations.

Discovery Queries:
- site:greatnonprofits.org [NICHE THEME]
- site:charitynavigator.org [NICHE THEME]
- [NICHE] charity "donate" "our supporters"
- [NICHE] nonprofit "donate" "thank you to our"
- [NICHE] foundation "donors"
- [CITY] [NICHE] charity "donate"

Output Table:
| Charity | Primary Website | Donation Page URL | Confirmed Outlinking Supporters Page URL | Min Donation Displayed | Relevance Justification |

Outreach Draft:
Write a warm, concise email introducing my business, expressing genuine alignment with their initiative, offering a donation, and politely asking for inclusion on their supporter roster with a backlink to [URL]. Leave the contribution amount as [AMOUNT].

Next Action: Make the donation through the verified portal, then track placement on the supporter directory.

---

## 2. Niche Edits (Contextual Link Insertions)

Secure placements inside existing, established content that already ranks on Google.

Prompt to run:
You're my SEO outreach assistant.
Site: [URL]
Target Page to Link To: [TARGET URL]
Topic/Niche: [TOPIC]

Goal: Discover high-ranking, currently indexed articles related to [TOPIC] where a link to my target page serves as a natural, value-adding editorial citation.

Rules:
- Real, live articles only: every URL must be an article you located via web search this session.
- Exclude link directories, content farms, and direct competitors' commercial pages.
- Target established, active blogs or industry resources that already feature outbound contextual references.
- One URL per domain. Star your top 3 strongest opportunities.

Discovery Queries:
- [TOPIC] guide -site:[MY DOMAIN]
- [TOPIC] intitle:[TOPIC] blog
- [TOPIC] "last updated" (2025..2026)
- [SUBTOPIC] resource guide -site:[MY DOMAIN]

Output Table:
| Target Site | Article URL | Exact Quoted Sentence for Placement | Suggested Anchor Text (Natural, non-exact-match) | Editorial Justification (How my link improves the section) | Contact (Verified email or form URL) |

Outreach Draft:
Write a high-converting, 4-sentence outreach pitch for the top pick. Reference the specific article title, quote the exact sentence, explain why citing my resource makes their article more complete, and include a [PRICE / COLLABORATION] placeholder in case an editorial fee is requested.

Next Action: Send personalized outreach directly to the editor or site owner.

---

## 3. Contextual Link Swaps (Non-Reciprocal)

Collaborate with non-competing peers in your vertical to exchange contextual references.

Prompt to run:
Site: [URL]
Target Vertical: [NICHE]

Goal: Identify 15-20 high-quality, non-competing websites within [NICHE] or adjacent sectors that maintain active, authoritative blogs suitable for a contextual link collaboration.

Rules:
- Real, established businesses and publications only; discard PBNs, link exchanges, and sites with spammy outbound patterns.
- Ensure the candidates are NOT direct business competitors (they must serve the same broader audience with complementary services).
- Prioritize non-reciprocal 3-way models (Site A -> Site B, Site B -> Site C) over direct reciprocal 2-way links.
- Star your top 3 safest fits.

Output Table:
| Site Name | Website URL | Audience Overlap | Direct Competitor? (Must be "No") | Recommended Exchange Type (3-Way / Contextual Partner) | Contact Method |

Outreach Draft:
Compose a professional partnership proposal for the top candidate offering a mutual contextual reference between relevant, already-indexed pieces of content. Emphasize relevance, strict contextual placement (no sitewide or footer links), and mutual audience value.

---

# A TIER

## 4. Guest Contribution Prospecting

Pitch original editorial insights to relevant industry publications.

Prompt to run:
You're my guest-post prospecting assistant.
Niche: [NICHE]
Site: [URL]
Target Page to Link To: [TARGET URL]

Goal: Find active, high-standard industry blogs that welcome contributed expert articles, along with personalized pitch angles.

Rules:
- Real, verified contributor guidelines only. Every opportunity must include an active submission guidelines link.
- Skip automated submission sites, generic article directories, and link-selling farms.
- Star your top 5 targets.

Discovery Queries:
- inurl:"write for us" [NICHE]
- inurl:"guest post" [NICHE]
- [NICHE] "contributor guidelines"
- [NICHE] "submit an article"
- [NICHE] "guest post guidelines"
- [NICHE] intitle:"write for us"

Output Table:
| Site Name | Guidelines URL | Core Submission Requirements (Word count, topics, link policy) | Contact (Email or direct form) |

Pitches:
For each of the top 5 starred sites, supply:
1. A tailored 3-sentence email pitch to the editor.
2. 3 original, non-generic article headline ideas designed around gaps in their current content, each indicating where [TARGET URL] naturally fits as a citation.

---

## 5. Niche & Local Directory Citations

Build essential citation foundations across industry-specific and regional hubs.

Prompt to run:
Business: [BUSINESS NAME + VALUE PROPOSITION]
Industry Category: [SaaS / AGENCY / LOCAL SERVICE / ECOMMERCE]
Niche: [NICHE]
Location: [CITY/REGION IF APPLICABLE]
Site: [URL]

Goal: Identify 25+ legitimate, reputable citation platforms, vertical registries, and trade directories where this business belongs, and prepare consistent submission copy.

Rules:
- Real directories only (no automated "mass submission" blast sites).
- Classify pricing (Free vs. Paid tier) and link attribute (dofollow / nofollow / unknown).
- Star your top 5 highest-priority listings.

Discovery Categories:
- Specialized vertical directories for [NICHE]
- SaaS/Product platforms (if tech): G2, Capterra, AlternativeTo, SaaSHub, Product Hunt
- Regional / Local platforms (if local): Google Business Profile, Chamber of Commerce, regional business alliances, Yelp
- Trade bodies, certified associations, and accreditation registries

Output Table:
| Directory Name | Direct Submission URL | Fee Model (Free / Paid) | Link Rel (Dofollow / Nofollow / Unknown) | Required Information (Logo, fields, character limits) | Target Category |

Standardized Listing Copy:
Provide standardized copy to maintain consistent NAP/entity data across all registrations:
- Single-Sentence Hook / Tagline: (Under 80 characters)
- Short Description: (Exactly 50 words)
- Full Description: (150 words highlighting unique capabilities and social proof)
- Core Category Tags: (5 targeted terms)
- Exact Name, Address, Phone (NAP) & URL block (if local)

---

## 6. PR & Media Announcement Engine

Transform genuine business developments into syndicated news citations.

Prompt to run:
Goal: Draft a concise, publication-ready press release announcing: [ANNOUNCEMENT / LAUNCH / MILESTONE].
Company: [COMPANY NAME], [1-sentence description].
Verified Facts: [WHAT HAPPENED / WHY IT MATTERS / KEY DATA POINTS / FOUNDER QUOTE / RELEASE DATE].

Rules:
- Use ONLY the facts provided above. Do not hallucinate metrics, background achievements, or quotes. Use placeholders (e.g., [METRIC]) for missing details.
- Maintain an objective, journalistic AP-style tone. Eliminate sales hyperbole ("revolutionary", "game-changing").

1. Newsworthiness Audit:
Provide a 1-sentence evaluation of the sharpest journalistic hook for this story.

2. Press Release Copy (~400 words):
- FOR IMMEDIATE RELEASE Header & Dateline
- High-Impact Headline & Sub-headline
- Executive Lead Paragraph (Who, what, when, where, why)
- Operational Body & Data Context
- Direct Executive Quote
- Boilerplate "About [COMPANY NAME]"
- Media Contact Information block

3. Distribution Targets:
- 4-sentence pitch email to beat reporters/editors.
- 5-8 verified trade reporters, specialized niche newsletters, or vertical tech outlets covering [NICHE] with direct profile links.

---

# B TIER

## 7. High-Authority Profile Footprints

Establish branded entity foundations and link diversity across top-tier platforms.

Prompt to run:
Site: [URL]
Business: [NAME + SERVICES]
Vertical: [NICHE]

Goal: Identify 20 reputable, high-trust platforms to build complete public profiles that link back to my primary website.

Rules:
- Active, recognized platforms only; supply direct registration URLs.
- Dofollow transparency: explicitly identify whether links are followed or nofollow (both are valuable for entity building and link velocity diversity).

Categories to Cover:
- Engineering / Community: GitHub, Dev.to, Stack Exchange, Kaggle
- Corporate / Ecosystem: Crunchbase, Wellfound, Trustpilot, Dealroom
- Editorial / Thought Leadership: Medium, Substack, Hashnode
- Niche-specific professional registries in [NICHE]

Output Table:
| Platform Name | Profile Link Location | Link Type (Dofollow / Nofollow) | Signup URL | Notes |

Bio Copy:
- Concise Bio: (Under 160 characters for social/micro profiles)
- Extended Bio: (300 words detailing background, accomplishments, and focus)
- Target URL and Anchor format

---

## 8. Expired Domain Vetting (PBN / Asset Analysis)

Audit expired domain opportunities for history, toxicity, and clean backlink equity.

Prompt to run:
Goal: Audit candidate expired or auction domains in the [NICHE] space for brand acquisition or 301 redirection.
Candidate Domain: [DOMAIN NAME] (or locate 3-5 potential candidates via auction marketplaces).

Rules:
- Do not make unverified claims regarding domain metrics without direct tools. Present all findings as candidates requiring verification.
- Enforce strict negative filters: immediately disqualify candidates with prior adult, casino, pharmaceutical, foreign anchor spam, or aggressive PBN footprints.

Audit Matrix:
1. Historical Topical Alignment: (Evaluate past snapshots via Wayback Machine)
2. Anchor Profile Health: (Check for automated spam footprints or unnatural exact-match distributions)
3. Historical Index Status: (Check Google cache/index remnants)
4. Red Flag Checklist: (Flag historical redirects, spammy subdomains, or topic changes)
5. Verdict: (Clean Candidate / High Risk / Disqualified)

---

## 9. Parasite SEO (High-Authority Publication Publishing)

Rank immediately on high-authority external domains for competitive commercial terms.

Prompt to run:
Goal: Produce a comprehensive article engineered to rank on a high-authority publication platform (e.g., Medium, LinkedIn Pulse, Dev.to) for the target search query: "[KEYWORD]".

Requirements:
- Target Search Intent: Commercial investigation / solution comparison.
- Length: ~1,200 words of structured, actionable analysis.
- Clear heading structure (H1, H2, H3) with comparison tables and bullet points.
- Include exactly ONE natural, high-relevance editorial citation linking back to [MY TARGET URL].
- Provide an optimized title, meta-style summary, and full Markdown article text ready for copy-paste.
- Reminder: Parasite SEO is designed to capture SERP real estate via external domain authority, even when the outgoing link is nofollow.

---

## 10. Unified Social Entity Setup

Deploy consistent branding, handles, and entity links across key social channels.

Prompt to run:
Business Name: [NAME]
Value Proposition: [WHAT YOU DO / WHO YOU SERVE]
Website: [URL]

Goal: Produce consistent, platform-compliant bio copy and account handles for deployment across all major networks.

Requirements:
Generate optimized copy blocks tailored to each platform's character limits and tone:
- X (Twitter): (Max 160 characters, include link)
- LinkedIn Company Page: (Tagline under 120 chars, About summary under 2,000 chars)
- YouTube Channel: (Channel description under 1,000 chars + links block)
- GitHub / Dev Platform: (Bio under 160 chars + README profile summary)
- Instagram / TikTok: (Bio under 150 chars + link CTA)

Output: Format each platform into a copy-paste snippet containing handle recommendations, bio text, and the link field.

---

# THE BIG MOVERS

## 11. Broken Link Reclamation

Identify dead external links on authoritative resource lists and pitch your replacement.

Prompt to run:
You're my broken-link-building assistant.
Niche: [NICHE]
Replacement Page: [URL]
Content Covered: [DETAILED DESCRIPTION OF YOUR PAGE]

Input Provided: [COMPETITOR RESOURCE URL, OR PASTE A LIST OF EXTRACTED OUTBOUND RESOURCE LINKS]

Rules:
- Verification Mandatory: only label an outbound link as "broken" if you actively request the URL and encounter an HTTP 404, DNS failure, or parked/dead domain page. If unverified, mark as "Unchecked".
- Topical Match: only pitch [URL] if it offers an exact, high-quality replacement for the dead resource.

Discovery Queries (if locating resource hubs from scratch):
- [NICHE] intitle:resources
- [NICHE] inurl:links
- [NICHE] "useful resources"
- [NICHE] "recommended tools"

Output Table:
| Host Resource Page | Dead Outbound URL | HTTP Status (404 / Dead Domain / Parked) | Anchor Text of Broken Link | Replacement Fit Score (1-10) | Site Contact (Email / Form URL) |

Outreach Pitch:
Draft a courteous notification email to the webmaster pointing out the specific broken link, citing the exact page location, and proposing [URL] as a relevant replacement to save them maintenance time.

---

## 12. Expired Domain 301 Redirection Mapping

Safely consolidate equity from a relevant acquired domain into your existing architecture.

Prompt to run:
Goal: Build a granular 301-redirect mapping plan for an acquired expired domain: [ACQUIRED DOMAIN] -> [DESTINATION SITE URL].

Rules:
- Relevance Constraint: verify that the historical topic matches the destination site. If irrelevant, warn of algorithmic devaluation risks.
- Avoid Blanket Homepage Redirects: mapping every legacy URL to the root domain triggers soft-404 flags. Every page must map to its closest topical equivalent.

Process:
1. Reconstruct historical top URLs from Wayback Machine archives or prior sitemaps.
2. Build a URL redirect matrix: Legacy URL -> Best Matching Destination URL.
3. For pages with no topical equivalent, designate an HTTP 410 Gone or omit redirection.

Server Configuration Delivery:
- Apache `.htaccess` RewriteRule block
- Nginx `rewrite` / `return 301` configuration block
- Cloudflare Bulk Redirect CSV format