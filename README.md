# A live DTC storefront (leveraged Shopify AI toolkit)

**Chronic Cardio · Venture-launch project, Innovator (MGT 421), Yale SOM · Spring 2026**

For my MBA venture-launch, I worked on finding a gap in the endurance fueling market, drawing from my own endurance running journey. Shopify store — [chroniccardio.com](https://chroniccardio.com) — working solo, with Shopify's AI toolkit and Claude Code.

| **14** | open-source fuel recipes published, with full formulation math |

## Context

Chronic Cardio is the venture I built in Yale SOM's Innovator course: a three-ingredient endurance gel (honey, tapioca syrup, sea salt) for athletes tired of $3+ sachets with fifteen-ingredient labels — a recipe I had already race-tested on a self-supported 100K. The course asks you to actually launch, so the brand needed a real direct-to-consumer storefront: product and checkout, the science behind the formulation, an open-source recipe library, and a way to capture early customers.

## The problem

What existed was a brand system and a static waitlist page on Vercel. Everything that makes e-commerce real was missing: a product with a purchase flow, customer records, forms, content pages. Shopify theme development (Liquid templates, nested block architecture) is its own specialty, and I'm not an engineer. The brand made it harder: a zine/punk visual system — Signal Orange, monospace type, hard 3px borders, paper-grain texture — that fights every default a polished theme ships with.

## What I built

A production storefront on Shopify's Horizon theme, migrated from Vercel over a weekend using Shopify's AI toolkit, then extended page by page with Claude Code:

- **Custom theme, real brand system:** custom Liquid sections and templates with the brand encoded as CSS design tokens, overriding stock styling everywhere — if it looks like a default theme, it's wrong.
- **Commerce with a batch mechanic:** the $15 Energy Pack (10 sachets) runs on a pre-order flow with a public counter toward the first 10,000-sachet production batch — 1,300+ sachets committed, no charge until it ships.
- **Lead capture wired into the CRM:** waitlist and sample-request forms write tagged customer records directly into Shopify — no third-party form tools, nothing to reconcile later.
- **Content that does marketing work:** a science page on the formulation, and an open-source library of 14 endurance-fuel recipes with the full formulation math — the brand's "nothing to hide" position, shipped as product.
- **A companion app:** an MIT-licensed [training-plan builder](https://github.com/amankrai28/chronic-cardio-train), live at [train.chroniccardio.com](https://train.chroniccardio.com/).

## Keeping AI safe on a production store

The interesting part isn't that AI wrote Liquid. It's the harness that makes AI-assisted work safe on a store real customers use:

- **Git first, Shopify downstream.** No file reaches the store that isn't committed. Every change ships to a fresh unpublished test theme, gets verified on a preview URL, and only then gets published — the previous live theme stays one click from restore.
- **An operating manual in the repo.** A `CLAUDE.md` documents the workflow rules and a "verified working state" log of patterns that are confirmed working in production, so no AI session "fixes" something that isn't broken.
- **Tests for the things that regress silently:** Playwright checks for brand tokens rendering, forms creating correctly-tagged customers, responsive breakpoints, and nav integrity.

## Where it stands

The store is live at [chroniccardio.com](https://chroniccardio.com), taking committed pre-orders against the first production batch, with the waitlist and sample pipeline feeding Shopify's CRM and the open-source pillar (recipes + training app) published.

## What I learned

AI tooling collapsed the distance between a brand system and a production storefront — a weekend instead of a contractor engagement. But the speed only holds because of process: version control as the source of truth, staged deploys, and written-down verified state are what let a non-engineer move fast on a real store without breaking it. The same lesson as every operations job I've had, in new clothes: the system around the work matters more than any single piece of work.

---

> The storefront's theme code lives in a private repo because it carries store configuration. This case study and the live site are the public artifacts.

More of my work: [github.com/amankrai28](https://github.com/amankrai28) · [LinkedIn](https://linkedin.com/in/amakrai)
