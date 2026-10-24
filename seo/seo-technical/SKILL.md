---
name: seo-technical
description: Analyze technical SEO, crawlability, indexability, security headers, Core Web Vitals (LCP/INP/CLS), and JavaScript rendering. Use when evaluating robots.txt, AI crawlers (ClaudeBot, GPTBot, PerplexityBot), canonical tags, redirect chains, mobile optimization, or auditing site performance.
argument-hint: "[target URL or list of URLs to audit]"
---

# Technical SEO Specialist & Engine Auditor

Audit technical SEO health, indexability, crawl accessibility, and rendering integrity. Prioritize root-cause architectural issues over superficial checklist items.

---

## Core Audit Protocol

Execute these 8 inspection stages in order for every target URL:

1. **HTML Source Inspection**: Fetch raw HTML (`curl -sL <URL>`) and compare directly against the rendered client DOM.
2. **Crawl & Discoverability**: Validate `robots.txt`, XML sitemaps, and directory hierarchy.
3. **Indexability & Meta Directives**: Verify canonical tags, `meta robots`, OpenGraph, and JSON-LD schema.
4. **Security & Protocol Headers**: Check response headers via `curl -I <URL>`.
5. **URL Architecture & Redirection**: Trace hop counts, trailing slashes, and HTTP-to-HTTPS redirects.
6. **Mobile Optimization & Layout**: Evaluate responsive viewport rules and touch target spacing.
7. **Core Web Vitals Assessment**: Analyze LCP subparts, visual stability (CLS), and interactivity (INP).
8. **AI Crawler Directives**: Confirm deliberate allow/block rules for modern LLM scrapers.

---

## 1. Core Web Vitals Reference Standards

Evaluate real metric thresholds. Never reference deprecated metrics like First Input Delay (FID), which was fully sunset.

| Metric | Target (Good) | Needs Improvement | Poor | Critical Subparts / Root Causes |
| :--- | :---: | :---: | :---: | :--- |
| **LCP** (Largest Contentful Paint) | **< 2.5s** | 2.5s – 4.0s | > 4.0s | **TTFB**: < 800ms<br>**Resource Load Delay**: < 100ms<br>**Resource Load Duration**: < 700ms<br>**Element Render Delay**: < 50ms |
| **INP** (Interaction to Next Paint) | **< 200ms** | 200ms – 500ms | > 500ms | Long JS execution tasks (> 50ms), heavy main-thread DOM reflows, event listener blocking. |
| **CLS** (Cumulative Layout Shift) | **< 0.1** | 0.1 – 0.25 | > 0.25 | Images/ads missing explicit `width`/`height` attributes, dynamic content injection above the fold, FOIT/FOUT web fonts. |

---

## 2. Security & Protocol Headers Checklist

Run `curl -I <URL>` and verify the presence and configuration of these response headers:

| Header | Required Value | Severity if Missing |
| :--- | :--- | :--- |
| **Strict-Transport-Security** | `max-age=31536000; includeSubDomains; preload` | High (HTTPS enforcement) |
| **X-Content-Type-Options** | `nosniff` | Medium (MIME-type sniffing) |
| **X-Frame-Options** | `DENY` or `SAMEORIGIN` | Medium (Clickjacking) |
| **Referrer-Policy** | `strict-origin-when-cross-origin` | Low |
| **Content-Security-Policy** | Configured CSP policy | Medium / High |
| **Permissions-Policy** | `geolocation=(), camera=(), microphone=()` | Low |

---

## 3. Modern AI Crawler Rules (`robots.txt`)

Audit AI agent access rules. Distinguish between model training scrapers and live search indexing/citation crawlers:

| Scraper / Bot | Purpose | Directive Guidance |
| :--- | :--- | :--- |
| `ClaudeBot` | Anthropic model training scraper | Allow or block based on data consent. |
| `Claude-SearchBot` | Claude web search & discovery | **Allow** if you want your site cited in Claude Search. |
| `Claude-User` | Live web fetch initiated by Claude user | **Allow** for user interactions. |
| `GPTBot` | OpenAI model training crawler | Allow or block based on training policy. |
| `OAI-SearchBot` | SearchGPT indexer & citations | **Allow** for ChatGPT search engine citations. |
| `PerplexityBot` | Perplexity search indexing & answers | **Allow** to be referenced in Perplexity answers. |
| `Google-Extended` | Gemini training & grounding | Blocking does **not** remove you from Google Search or AI Overviews (standard `Googlebot` controls those). |
| `CCBot` | Common Crawl dataset scraper | General AI training dataset collector. |

---

## 4. JavaScript Rendering & Architecture Check