# PRD: Visual Stories
### FinTech Consumer Content Hub — Phase 4: Delight

---

## Overview

This repository contains a feature-level Product Requirements Document for Visual Stories — a short-form, mobile-optimized content format built on Adobe Experience Manager (AEM) for a FinTech consumer content hub.

Visual Stories is the first feature from the post-MVP Delight phase of the content hub roadmap, and the first format on the hub explicitly designed for social referral acquisition. The feature was driven by an analytics-identified gap: social referral traffic was growing slowly despite increased posting frequency, with root cause analysis pointing to a format mismatch rather than a content quality problem.

📄 **[Read the full PRD →](./prd-visual-stories.md)**

---

## What This Demonstrates

This document shows how I approach **feature-level product work within an established platform** — a common PM challenge that requires working within existing technical constraints, content models, and stakeholder workflows rather than building from scratch.

**Problem framing from data** — The feature is grounded in a concrete analytics-identified gap: social referral traffic was growing slowly despite increased posting frequency. The PRD surfaces the root cause (format mismatch, not content quality) and proposes a targeted solution rather than a generic "add a new format" ask.

**Two-type content model** — Visual Stories required differentiating Editorial and Merchandising story types with distinct CTA pathing logic. Capturing this as a formal distinction — rather than a series of optional fields — reflects how content strategy decisions translate into authoring constraints and content models.

**Constraint-driven scope decisions** — Several decisions are explicitly grounded in technical or UX constraints: swipe gestures excluded to avoid conflict with native mobile browser gestures; cinemagraphs deferred due to accessibility requirements and player infrastructure; companion article enforced as a required field to prevent orphaned stories. The PRD documents the *why* behind each, not just the *what*.

**Lightweight integration over net-new components** — Rather than specifying a dedicated homepage shelf, Visual Stories surface through existing Editor's Picks and Hot Off the Press sections as standard article cards — a deliberate scope decision that reduces engineering effort and respects the existing content architecture.

**Phased roadmap that informs architecture** — The Future Considerations section documents capabilities deferred to Phases 2–4 (cinemagraphs, motion graphics, polls, native app), explicitly framed to ensure MVP architecture doesn't foreclose future expansion.

---

## Document Metadata

| | |
|---|---|
| **Product** | Consumer Content Hub — Visual Stories |
| **Document Type** | Feature PRD |
| **Surface** | Mobile web (primary), desktop web (secondary) |
| **Platform** | Adobe Experience Manager (AEM) |

---

## Related Artifacts

This PRD is part of a series documenting the FinTech Consumer Content Hub initiative:

| Artifact | Description |
|---|---|
| [PRD: FinTech Consumer Content Hub (MVP)](https://github.com/thedmons/prd-content-hub) | Platform PRD this feature builds on — content model, taxonomy, SEO, phased roadmap |
| [System Design: AEM Component Architecture](https://github.com/thedmons/system-design-content-hub) | Technical architecture underlying the hub — component library, JCR taxonomy, caching, analytics |
