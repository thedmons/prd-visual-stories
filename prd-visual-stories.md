# PRD: Visual Stories
### fintech.com/stories — Delight Phase Feature

---

| | |
|---|---|
| **Product** | Consumer Content Hub — Visual Stories |
| **Document Type** | Product Requirements Document (PRD) |
| **Status** | Completed |
| **Date** | Q1 2024 |
| **Surface** | Mobile web (primary), desktop web (secondary) |
| **Author** | Digital Product |
| **Stakeholders** | Marketing Lead · UX Design · IA/AEM SME · AEM Author · SEO · Social |
| **Related Docs** | [PRD: FinTech Consumer Content Hub](https://github.com/thedmons/prd-content-hub) · [System Design: AEM Architecture](https://github.com/thedmons/system-design-content-hub) |

---

## Table of Contents

1. [Overview](#1-overview)
2. [Background & Strategic Context](#2-background--strategic-context)
3. [Goals & Success Metrics](#3-goals--success-metrics)
4. [Scope](#4-scope)
5. [User Personas](#5-user-personas)
6. [Story Types](#6-story-types)
7. [Functional Requirements](#7-functional-requirements)
8. [Content Model](#8-content-model)
9. [Non-Functional Requirements](#9-non-functional-requirements)
10. [Dependencies & Risks](#10-dependencies--risks)
11. [Future Considerations](#11-future-considerations)
12. [Open Questions](#12-open-questions)

---

## 1. Overview

Visual Stories is a new short-form content format for the FinTech consumer content hub — a full-bleed, mobile-optimized experience designed for consumers who discover financial content through social channels and prefer snackable formats over long-form articles.

Each Visual Story is a 3–7 slide sequence (targeting under 1 minute of total read time) covering a single financial topic (e.g., "5 signs you're ready to buy a home," "What happens to your credit score when you apply for a loan"). Slides support static images, GIFs, and short video clips. Stories are authored in AEM, published to fintech.com/stories/visual-stories/, shareable as direct links, and structured for social Open Graph previews.

Visual Stories come in two types — **Editorial** and **Merchandising** — each with distinct CTA pathing rules (see Section 6). On the content hub, Visual Stories are surfaced as article cards with "Visual Story" noted in the topic tag — consistent with the existing article card pattern.

This is the first delivery of Phase 4 — Delight from the content hub post-MVP roadmap, and the first content format on the hub explicitly designed for social referral traffic.

---

## 2. Background & Strategic Context

### 2.1 The Gap This Fills

The content hub launched with long-form articles as its only content format. Analytics from the first year showed a consistent pattern: articles perform well for organic search (high time-on-page, good scroll depth) but perform poorly as shareable, socially-distributed content.

When articles were shared on social channels, click-through rates were low. Qualitative feedback from the social team identified the core issue: long-form article previews don't translate to social contexts. A 2,500-word article on mortgage qualification shared on Instagram doesn't signal "quick read" — it signals "homework."

Meanwhile, social referral traffic to the hub — which the content strategy identified as a key acquisition channel — had grown only marginally year-over-year despite increased social posting frequency.

### 2.2 The Opportunity

Short-form visual content (Instagram Stories, TikTok, Snapchat, LinkedIn Carousels) has demonstrated high engagement with financial literacy topics. The audience exists and is receptive — the format mismatch is the barrier.

Visual Stories creates a native web equivalent of the social story format: visually led, concise, and shareable as a link that resolves to a purpose-built mobile experience rather than a desktop article layout.

The opportunity extends beyond acquisition: Visual Stories capture additional customer engagement, develop deeper relationships with consumers, and create a repeatable format for connected marketing campaigns.

### 2.3 Connection to Long-Form Content

Visual Stories are not a replacement for long-form articles — they are a companion and entry point. Each story ends with a CTA linking to the full article on the topic, creating a funnel from social-referred snackable content into deeper hub engagement. Merchandising stories additionally path users directly to relevant product pages.

---

## 3. Goals & Success Metrics

### 3.1 Goals

- Launch a mobile-first short-form content format designed for social referral acquisition
- Increase social referral traffic to the content hub within 90 days of launch
- Create a repeatable, author-friendly story creation workflow in AEM
- Establish Visual Stories as a top-of-funnel format that drives downstream article and product engagement

### 3.2 Success Metrics

| Metric | Baseline | Target | Result | Measurement |
|---|---|---|---|---|
| Story clickthrough rate (to article or product) | Establish at launch | Increase vs. pre-launch baseline | Baseline established; directional lift vs. pre-launch | Adobe Analytics |
| Story impressions (monthly) | 0 | Establish baseline in month 1 | Baseline established in month 1 | Adobe Analytics |
| Social referral sessions to content hub (monthly) | Establish at launch | Measurable lift at 90 days | +87% overall content hub sessions at 90 days (198.9K → 372.6K); +25.2% YoY growth | Adobe Analytics |
| Mobile traffic share | 62.9% (pre-launch) | Directional increase | 65.5% at 90 days (YTD) | Adobe Analytics |
| Stories published per month | 0 | 6–8 (targeting 2/week) | Baseline established | Content calendar |

> **Attribution note:** Session and traffic growth reflects overall content hub performance in the 90 days following Visual Stories launch (Dec 2023 – Mar 2024) — not attributed solely to this feature. Mobile share increase is directionally consistent with a format designed for mobile social audiences.

---

## 4. Scope

### 4.1 In Scope

- **Visual Story page template:** New AEM page template at `/stories/visual-stories/[story-slug]`
- **Story slide component:** Full-bleed image, GIF, or gradient background; embedded video player; headline; body text; optional stat callout
- **Story navigation:** On-screen arrow buttons (mobile and desktop); tap-zone navigation (left/right half of screen); progress bar; back to previous slide supported
- **Story end card:** Final slide with topic summary + CTA(s) per story type rules (see Section 6)
- **Story index page:** `/stories/visual-stories/` — grid of published stories rendered as article cards with "Visual Story" topic tag
- **Homepage discovery:** Visual Stories surface on the hub homepage within the existing **Editor's Picks** and **Hot Off the Press** sections as standard article cards — no new homepage component required
- **SEO + Open Graph:** Unique meta title, description, and social preview image per story page
- **AEM authoring:** Author-configurable slide-by-slide content via Touch UI dialog; mobile preview before publish
- **Analytics:** Story view (impressions) and CTA click events

### 4.2 Out of Scope (V1)

- Swipe gesture navigation (native mobile browser gestures may conflict with story navigation — explicit on-screen controls used instead)
- Cinemagraph / looping video backgrounds (deferred to Phase 2 due to accessibility considerations and player infrastructure requirements — see Future Considerations)
- Native app integration (web only)
- Story reactions or comments
- Stories algorithm / personalized story feed
- Instagram or Snapchat native story publishing (social teams screenshot and repost manually)
- User-generated stories
- Dynamic/interactive media: polls, quizzes, infographics (see Section 11 — Future Considerations)

---

## 5. User Personas

### 5.1 The Social-Referred Consumer

Arrives from a social channel (Instagram, LinkedIn, TikTok link in bio) after seeing the story shared by the brand's social team or a personal finance influencer. They are on mobile, likely in a scroll session, and have low commitment to reading but high receptivity to visual financial content. They will consume the story if it loads fast, looks native to their context, and doesn't feel like a website.

- **Needs:** Instant load, no friction, clear navigation
- **Success:** Completes story, clicks through to article or product CTA

### 5.2 The Hub Regular

An existing content hub visitor who encounters a Visual Story card on the homepage — surfaced within the existing **Editor's Picks** or **Hot Off the Press** sections — or while browsing the article index. Visual Stories appear in these sections as standard article cards with "Visual Story" noted in the topic tag; no dedicated homepage component is required.

- **Needs:** Clear format signal on the article card, easy return to article browsing after story
- **Success:** Opens story from a homepage or index card, clicks through to related article or product

### 5.3 The AEM Content Author

A marketing team member responsible for creating and publishing Visual Stories. They are not engineers. They need a slide authoring experience that doesn't require design software — background selection, headline input, body text, and stat callout fields in a standard AEM dialog.

- **Needs:** Fast authoring, predictable output, mobile preview before publish
- **Success:** Authors and publishes a complete story in under 45 minutes

---

## 6. Story Types

Visual Stories come in two distinct types. Story type is set at the page level by the author in AEM and determines the CTA pathing rules that apply across slides and the end card.

### 6.1 Editorial Stories

Editorial stories visually summarize the key points of a long-form article. They are the most common story type.

**Purpose:** Quickly express article focus; drive readers into the full article experience.

**CTA pathing rules:**
- The primary CTA is always **"Read the full article"** — linking to the companion editorial article. This CTA is typically placed on the final screen but may appear on any slide where the connection is strong.
- A secondary CTA may link to a **merchandising article** related to the story's topic. This CTA will match the Related Article merchandising piece used in the full editorial article.

**Companion article:** Required field. Story cannot be published without a valid editorial article reference.

### 6.2 Merchandising Stories

Merchandising stories highlight key product benefits in an easily digestible format. They are used less frequently than editorial stories.

**Purpose:** Sum up product value proposition; path users to the product or a supporting merchandising article.

**CTA pathing rules:**
- The primary CTA links to the **full merchandising article** — can be placed on any slide where the product connection is relevant.
- A secondary CTA links to the **relevant product page** — typically placed on the final screen but may appear on any slide making a strong product connection.

**Product CTA:** Optional but expected for merchandising stories. Author configures product CTA label and URL in AEM.

---

## 7. Functional Requirements

### 7.1 Story Page Template

| Feature | Description | Priority |
|---|---|---|
| Full-bleed slide layout | Each slide occupies 100vw × 100dvh; no chrome, no nav, no footer | P0 |
| Progress bar | Segmented bar at top showing X of Y slides; active segment fills left to right | P0 |
| Slide counter | "3 / 7" text display as secondary progress signal | P1 |
| Close / exit button | X button top-right returns user to referring page or hub index | P0 |
| On-screen arrow navigation (mobile) | Left arrow → previous slide; right arrow → next slide; explicit UI buttons | P0 |
| Tap-zone navigation (mobile) | Tap left half of screen → previous slide; tap right half → next slide | P0 |
| Click/arrow navigation (desktop) | Click right half → next; click left half → previous; keyboard arrow keys supported | P0 |
| No swipe gesture navigation | Swipe gestures are explicitly excluded; native mobile browser gestures (scroll, back) must not be intercepted | P0 |
| Story title (first slide) | First slide always shows story headline + topic tag | P0 |
| Keyboard accessibility | Full keyboard navigation: right arrow next, left arrow back, Escape exits | P0 |

### 7.2 Story Slide Component

| Feature | Description | Priority |
|---|---|---|
| Background — image | Author selects DAM image (16:9, auto-cropped to 9:16 on mobile) | P0 |
| Background — GIF | Author selects DAM GIF; loops silently; does not auto-advance slide | P0 |
| Background — embedded video | Author selects DAM video; renders via standard video player with play/pause controls; does not auto-advance slide; captions supported | P1 |
| Background — color | Author selects solid brand color from predefined palette | P0 |
| Background overlay | Semi-transparent dark gradient overlay on image/GIF/video backgrounds for text legibility — not author-configurable | P0 |
| Headline | Max 60 characters; large, bold; always white on overlay | P0 |
| Body text | 2–5 lines / 100–200 characters; medium weight; white; optional field | P0 |
| Stat callout | Optional: large number + label (e.g., "3.5%" + "minimum down payment") — visually distinct callout block | P1 |
| Inline CTA | Optional mid-story CTA button per story type pathing rules (see Section 6) | P1 |
| Emoji / icon accent | Optional single emoji or icon above headline for visual variety | P2 |

### 7.3 End Card (Final Slide)

| Feature | Description | Priority |
|---|---|---|
| Story summary line | 1-sentence recap of the story's key takeaway | P0 |
| Primary article CTA | "Read the full guide →" or "Read the article →" per story type; required | P0 |
| Product CTA | Secondary CTA to product page — required for Merchandising stories, optional for Editorial | P1 |
| Share button | Native mobile share sheet (Web Share API); fallback to copy-link on unsupported browsers | P1 |
| Related stories | 2 thumbnail links to other Visual Stories on similar topics | P2 |

### 7.4 Stories Index Page (/stories/visual-stories/)

| Feature | Description | Priority |
|---|---|---|
| Article card grid | Visual Stories rendered as standard article cards; "Visual Story" surfaced in topic tag | P0 |
| Topic filter | Filter stories by primary topic — same taxonomy as articles | P1 |
| Sort | Default: most recently published | P0 |

---

## 8. Content Model

Visual Story pages are stored as AEM pages under `/content/fintech/stories/visual-stories/`. Each story page contains an ordered list of slide nodes.

```
jcr:content/
  ├── storyTitle              (String — display title)
  ├── storySubtitle           (String — optional, shown on index card)
  ├── storyType               (String — "editorial" | "merchandising")
  ├── primaryTopic            (String — taxonomy path; "Visual Story" tag applied at page level)
  ├── thumbnailImage          (String — DAM path, used for article card + OG image)
  ├── thumbnailAlt            (String)
  ├── metaTitle               (String)
  ├── metaDescription         (String)
  ├── companionArticle        (String — path to companion article; required)
  ├── productCtaLabel         (String — end card product CTA label; required for merchandising)
  ├── productCtaLink          (String — end card product CTA URL; required for merchandising)
  │
  └── slides/                 (ordered node list, 3–7 slides)
        ├── slide_1/
        │     ├── backgroundType    (String — "image" | "gif" | "video" | "color")
        │     ├── backgroundAsset   (String — DAM path for image/GIF/video)
        │     ├── backgroundAlt     (String — if image or GIF)
        │     ├── backgroundColor   (String — brand color token, if type = color)
        │     ├── headline          (String — max 60 chars)
        │     ├── bodyText          (String — 100–200 chars, optional)
        │     ├── inlineCta/        (optional mid-story CTA)
        │     │     ├── ctaLabel    (String)
        │     │     └── ctaLink     (String)
        │     └── statCallout/      (optional)
        │           ├── statValue   (String — e.g., "3.5%")
        │           └── statLabel   (String — e.g., "minimum down payment")
        └── slide_2/ ...
```

---

## 9. Non-Functional Requirements

**Performance:** First slide must render within 1.5s LCP on a 4G mobile connection. Slides preload the next slide's background asset on arrival — not all slides at once. GIF and video assets are lazy-loaded. JavaScript bundle for story navigation is code-split and lazy-loaded separately from the main hub bundle.

**Navigation constraint:** The story experience must not intercept native mobile browser gestures (horizontal swipe for back navigation, vertical scroll). All story navigation is handled through explicit on-screen controls — left/right arrow buttons and tap zones — to avoid conflicts with browser and OS-level gestures.

**Accessibility:** Story navigation is fully keyboard-accessible. Progress bar includes `aria-label="Slide X of Y"`. Background images and GIFs include alt text. Embedded video slides include player controls (play/pause) and caption support; video does not auto-play or auto-advance the slide. User controls all navigation. Exit button is always reachable.

**SEO:** Story pages are indexable. Each story has unique title, meta description, and canonical URL. Structured data: `WebPage` type. Stories are included in XML sitemap. Slide-by-slide content is not individually indexable — only the story landing page is crawled.

**Open Graph:** Each story page outputs `og:image` (first slide thumbnail, 1200×630 crop), `og:title`, `og:description`. Twitter Card meta also included. This is the primary mechanism by which stories render correctly when shared on social platforms.

**Responsive behavior:** Story template renders full-bleed on all viewports. On desktop, the story is centered in a max-width container (430px — phone-width) with a blurred background fill on either side. This maintains the mobile-native feel on desktop without breaking the experience.

**Component reuse:** Implementation should leverage existing atomic AEM components where possible to minimize net-new component development.

---

## 10. Dependencies & Risks

| Dependency / Risk | Detail | Mitigation |
|---|---|---|
| Image/GIF asset production | Visual Stories require purpose-shot or licensed imagery at 9:16 ratio — existing DAM assets are predominantly 3:2. GIF assets require additional production overhead. | Marketing to confirm asset sourcing approach before launch; budget implications for motion assets |
| Author adoption | Stories are only valuable if published consistently — targeting 2/week | Content calendar commitment from Marketing before engineering sprint begins |
| Web Share API coverage | Native share sheet is not supported on all desktop browsers | Fallback to copy-link; acceptable degradation |
| Companion article requirement | End card CTA requires a published companion article or product page | Enforce companion article as required field in AEM dialog; cannot publish without a valid reference |
| Social team workflow | Stories require active distribution by the social team — product cannot control reach | Align with Social team pre-launch on posting cadence; provide 9:16 static preview image export from AEM for native re-posting |
| GIF DAM workflow | Authors will need guidance or tooling to upload and tag GIF assets correctly in the DAM | IA/AEM SME to define DAM tagging standards for GIF assets before authoring begins |

---

## 11. Future Considerations

These capabilities are out of scope for MVP but represent the natural evolution of the Visual Stories format. They are documented here to inform architecture decisions and ensure MVP does not foreclose future expansion.

| Capability | Description | Phase |
|---|---|---|
| Cinemagraphs (looping video backgrounds) | Looping video as a slide background alternative to static image/GIF. Deferred due to accessibility considerations and the additional player infrastructure required to support the format correctly. | Phase 2 |
| Motion graphics | Animated graphics and data visualizations within slides (CSS/Lottie animations) | Phase 2 |
| Polls and quizzes | In-story polls with results reveal on the next slide | Phase 3 |
| Interactive infographics | Tap-to-expand charts, annotated images, scrollable data within a slide | Phase 3 |
| Native app integration | iOS/Android app surface for Visual Stories | Phase 4 |

---

## 12. Open Questions

| Question | Owner | Status |
|---|---|---|
| Should stories be noindex initially and switched to indexable after social traffic data is assessed? | SEO | Closed — stories are indexable at launch |
| Should story URLs be date-stamped or evergreen? | SEO | Closed — evergreen URLs confirmed; no date in slug |
| How should story type (Editorial vs. Merchandising) be surfaced to users, if at all? | Design / Product | Closed — story type is not surfaced to end users; "Visual Story" topic tag is the only format signal |
| Is there appetite for a GIF asset upload workflow in the DAM, or will authors use existing tooling? | AEM Tech / IA SME | Closed — existing DAM tooling used; no new workflow required |
| In-hub discovery is intentionally limited to existing homepage sections (Editor's Picks, Hot Off the Press) and the article index for V1. Primary acquisition focus is social referral traffic. A dedicated discovery surface (e.g., a Visual Stories browse experience or filter) should be scoped as a follow-on phase as the story library grows. | Product / Marketing | Recognized gap — defer to future phase |
