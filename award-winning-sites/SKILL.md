---
name: award-winning-sites
description: How Sheha's studio designs and builds premium, conversion-first websites for small businesses (wedding and event vendors, print shops, coaching offers, local service businesses). Use this skill whenever the user asks to build, redesign, mock up or critique a website, landing page, homepage, sales page, quote calculator, inquiry flow or booking flow, mentions Nightingale, EDA, Event Decor Academy or B-Town as a reference, or says "like our other sites" or "award winning". Also use it when the user shares a brand palette, logo or Instagram and wants a site from it. It carries the house design system, the decision rules, reusable section and animation patterns, conversion tools, SEO and deploy checklists, and screenshots of past work.
---

# Award Winning Sites

The studio has shipped three sites that define its house style: **Nightingale Events** (wedding decor and florals, Toronto), **Event Decor Academy** (a coaching offer for decorators) and **B-Town Print Studio** (a large format print shop with self-serve quoting). Every new site should feel like a sibling of these: same bones, same confidence, a different skin.

The goal of each site is the same: make a small business look like the premium option before the visitor ever messages them, then remove every reason not to act. Awards follow from that, not the other way round.

## How to work

1. **Start from the brand, not the template.** Ask for or pull the logo, palette, Instagram, mood boards and the one sentence the owner would say about their business. Derive type and colour from those. Do not reuse another site's palette or typeface because it was pretty there. B-Town moved from Instrument Serif to a chunky grotesque the moment its logo arrived, because a print shop is a physical product and the elegant serif read as "our software product".
2. **Decide the hero before anything else.** It carries the site. Every site gets a scroll-stopping, animated hero that is *about the business*, not a stock video. See [references/motion.md](references/motion.md) for the three hero patterns we have shipped and how to pick one.
3. **Lay out the page from the section library.** Read [references/section-patterns.md](references/section-patterns.md) and pick the sections the business needs. Keep the rhythm: kicker, headline with one italic or highlighted turn, muted lede, then the content.
4. **Build the conversion tool early.** Each site has one self-serve tool that replaces an email thread: a budget planner, an application flow, an instant quote with a real-size preview. See [references/conversion-tools.md](references/conversion-tools.md). It is usually the thing the owner loves most.
5. **Ship a sample fast, then iterate live.** Build a single-file homepage, publish it as a hosted link the owner can open on their phone, and iterate from their reactions. Expect ten rounds of small changes. Keep each round pushed to git.
6. **Finish with SEO and launch.** Local SEO is table stakes for these clients. Follow [references/seo-and-launch.md](references/seo-and-launch.md).

Before building, skim [references/case-studies.md](references/case-studies.md) for the site closest to the new client's industry. It has screenshots by section and the decisions behind them.

## Design rules that hold across every site

These are the things the three sites share. Treat them as defaults you need a reason to break.

- **Warm paper, never pure white.** Backgrounds are cream or blush-tinted (#fbf3ea, #faf6ee, #fffdf6). Ink is a warm near-black, not #000. A fixed film-grain overlay at 6 to 7 percent opacity sits over everything.
- **One display face, one text face.** Display at a single weight with real character (Instrument Serif at 400, Fraunces, Bricolage Grotesque at 800). Text in a quiet grotesque (Hanken Grotesk, DM Sans, Inter Tight). Never more than two families.
- **Headlines turn once.** Every H1 and H2 has exactly one accent phrase: italic in the accent colour on the elegant sites, a yellow marker highlight on the playful one. Not two, not zero.
- **Kicker, headline, lede.** Sections open the same way every time: small uppercase kicker with a short rule before it, the serif headline capped around 16 characters wide, a muted lede capped at 52 characters. The repetition is the brand.
- **Pills everywhere.** Floating blurred nav in a pill. Pill buttons with a two-pixel lift on hover. Pill labels inside image frames. Pill chips for choices.
- **Rounded frames with label pills.** Photos and clips live in 20 to 32 px rounded frames, arch-topped when it suits the subject, with a small uppercase label pill sitting inside the frame's bottom corner.
- **Real proof, in its native form.** Testimonials are screenshots of the actual channel: WhatsApp and iMessage bubbles, Instagram DMs, a voice note with a waveform, Google review cards, room-reveal videos. Never a quote in a grey box with a stock headshot.
- **Big serif numbers as proof.** A proof bar under the hero with three numbers and short captions. Numbers do the persuading.
- **Dark glow sections for the money moment.** The pricing stack, the value receipt, the final CTA: ink background, two soft radial glows in brand colours, light type.
- **Native scroll, honest motion.** Fade-up reveals with a 70 ms sibling stagger, count-ups, a slow italic marquee, sticky split layouts. Never hijack the scroll on inner sections. Always respect prefers-reduced-motion. Full tokens and code in [references/design-system.md](references/design-system.md).
- **Mobile is a first-class layout.** Every grid collapses on purpose; hover-only interactions (flip cards) show both states on touch.

## How we make decisions

- **Match the energy of the product.** Services sold on taste (decor, florals, coaching) get the elegant serif and italics. Physical products and shops get chunky type, saturated brand colour and photography of the actual thing. The owner's reaction "it looks like our software product" means the energy is wrong.
- **The client's palette wins, the studio's taste finishes it.** Take the primary colour as given, then add one secondary from the brand board and one small "touch" accent (B-Town: yellow primary, mint secondary, a touch of blue for kickers and focus states).
- **Show, don't describe, in the hero.** Nightingale's silk curtain parts to reveal a real room. EDA's arch frames a real install with floating stat badges. B-Town's own printer prints the client's real signs in a loop. If the hero could be reused for another business, it is not finished.
- **One animated idea per section.** The hero gets the big one. Everything after it gets a reveal and at most one small delight (a marquee, a flip, a count-up).
- **Owner feedback is literal and visual.** Owners say things like "he looks sad", "too lanky", "the ff is cut off", "that right swipe". Fix exactly that, take a screenshot to confirm, push, and move on. Do not relitigate.
- **Placeholders are labelled.** Fake reviews, sample logos and guessed prices are marked as samples in the page itself so the owner never mistakes them for real.
- **Prices come from the owner.** Build the calculator with a visible rate table and swap in their numbers the moment they arrive (B-Town: $5 per sq ft direct, $3 for vendors, chosen by a dropdown).

## Copy voice

Short declaratives in second person. One specific number where one exists. The headline makes a claim; the lede says how. Examples from shipped sites:

- "Love is the greatest art, and we are its designers."
- "You're charging $3,000 for a $10,000 wedding. We fix that in 90 days."
- "Don't take our word for it. Take theirs."
- "See your price before you blink."
- "If you can think it, we can print it."

More in [references/copy-voice.md](references/copy-voice.md).

## Reference files

| File | Read it when |
|---|---|
| [references/case-studies.md](references/case-studies.md) | Starting a new site. Pick the closest industry and see the decisions and screenshots. |
| [references/design-system.md](references/design-system.md) | Setting tokens, type scale, buttons, nav, grain, reveal and marquee code. |
| [references/section-patterns.md](references/section-patterns.md) | Laying out the page. Each section with purpose, structure, screenshot and code notes. |
| [references/motion.md](references/motion.md) | Designing the hero or any animation. Three shipped hero mechanics with code. |
| [references/conversion-tools.md](references/conversion-tools.md) | Building a quote calculator, budget planner, one-question flow or real-size preview. |
| [references/copy-voice.md](references/copy-voice.md) | Writing headlines, ledes, CTAs, FAQ and SEO copy. |
| [references/seo-and-launch.md](references/seo-and-launch.md) | Meta, JSON-LD, local SEO, performance, Netlify deploy, handoff. |

Screenshots live in `assets/screenshots/` and are named `site-NN-section.jpg`.
