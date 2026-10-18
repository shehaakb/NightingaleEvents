# Section patterns

The library of sections we have shipped, in the order they usually appear. For each: what it does, when to use it, the structure, and a screenshot. Pick what the business needs; do not use all of them.

Every section opens with the same rhythm: `.kicker` then `.h2` (one accent turn) then `.lede`. Then its content.

## 1. Hero
The one section that must be unique to the business. Three mechanics in [motion.md](motion.md). Always includes: eyebrow line naming what and where, headline with one turn, a one-sentence lede, primary and ghost CTA, a small reassurance line with a ✦, and usually a proof bar.

![](../assets/screenshots/eda-01-hero.jpg)
![](../assets/screenshots/btown-01-hero.jpg)

## 2. Proof bar
Three big serif numbers with short captions, separated by hairlines, under the hero CTAs. Count up on load. Use real numbers; if none exist yet, use time-based promises (48h, 2–3 days) and $0 fees.

```html
<dl class="proof-bar"><div><dt>$42K</dt><dd>months in year two, up from $5K</dd></div>…</dl>
```

## 3. Marquee
Slow italic serif strip of services or promises, optionally rotated 1.2°. A divider that carries copy. Skip it for product shops if the owner finds it busy.

![](../assets/screenshots/nightingale-06-marquee.jpg)

## 4. Brands / trusted-by row
Two counter-scrolling rows of greyscale wordmarks that colour on hover, masked at the edges. Use sample wordmarks across many industries when the client has none yet and label them as samples.

![](../assets/screenshots/btown-03-brands.jpg)

## 5. Planner / quote band
A full-width coloured band right under the hero pointing at the conversion tool. Nightingale: olive band, centred serif headline, cream pill button.

![](../assets/screenshots/nightingale-03-planband.jpg)

## 6. Manifesto / story
Kicker, a long serif line, then a body paragraph next to three staggered photo frames (4:5, one pushed down). Ends with a second right-aligned serif line. Use for services sold on taste.

![](../assets/screenshots/nightingale-05-manifesto-frames.jpg)

## 7. Who it's for
Two columns: "For you if…" with green tick bullets, "Not for you if…" muted with red crosses. Qualifies and flatters at once. High-ticket offers only.

![](../assets/screenshots/eda-03-who.jpg)

## 8. Comparison
"Same wedding. Different price." A dashed, strikethrough "them" card beside a dark, slightly rotated "you" card with gradient price. Works for any premium-vs-cheap positioning.

![](../assets/screenshots/eda-04-premium.jpg)

## 9. Founder story
Arch-top photo or clip, kicker "I was you", first-person paragraphs, a signature line, then three stats on a hairline. Use when the owner is the brand.

![](../assets/screenshots/eda-05-story.jpg)

## 10. What we build / promise list (sticky split)
Left column sticky at 130 px with kicker, headline, lede and CTA; right column a list of cards that lift and rotate 0.4° on hover. Each card: small uppercase tag, serif H3, one sentence.

![](../assets/screenshots/btown-06-why.jpg)
![](../assets/screenshots/eda-06-build.jpg)

## 11. Timeline / process modules
`<details>` list with number, serif title, right-aligned tag; one open at a time; title italicises or recolours when open. Four to six items.

![](../assets/screenshots/eda-07-timeline.jpg)
![](../assets/screenshots/btown-07-design.jpg)

## 12. Love notes (proof section)
Headline "Don't take our word for it. Take theirs." Then, in order as available: a voice note card (dark, play button, waveform, transcript toggle), a 16:9 feature video, a row of 9:16 reveal clips, then real chat bubbles in a 3-column masonry (WhatsApp dark, iMessage light and dark, Instagram grey) and Google review cards with stars. Native styling per channel is the whole point.

![](../assets/screenshots/nightingale-07-love-voice.jpg)
![](../assets/screenshots/nightingale-09-love-chats.jpg)
![](../assets/screenshots/btown-08-love.jpg)

## 13. Gallery
Staggered 12-column grid of looping muted clips or photos in rounded frames with label pills. Lazy-load clips with `data-src` and an IntersectionObserver. For product shops add a second pill with "from $" on the right.

![](../assets/screenshots/nightingale-10-gallery.jpg)
![](../assets/screenshots/btown-05-gallery.jpg)

## 14. Behind the scenes
Four arch-top frames, alternate ones pushed down, each a clip of the owner working. Humanises a service brand.

![](../assets/screenshots/nightingale-11-atwork.jpg)

## 15. What we do: flip cards
3-column grid of tall cards (3:4). Front is a full-bleed photo with a dark fade and the title; back flips to a brand colour with two sentences and a "from" price. Stack both faces on touch devices.

![](../assets/screenshots/btown-09-what-we-do.jpg)
![](../assets/screenshots/btown-13-flip-hover.jpg)

## 16. Value stack receipt
Dark glow section, sticky intro on the left with a giant number, a cream "receipt" card on the right with serrated top and bottom edges (CSS mask), grouped rows with dotted leaders, bonus rows in accent, strikethrough total and a gradient price. The highest-converting section on EDA.

![](../assets/screenshots/eda-11-stack.jpg)

## 17. Service area (local SEO)
Kicker naming the city, headline "City's most reliable …", a 60-word paragraph that says the service and the cities in plain English, a chip row of towns, and a stylised map tile. Repeat the cities in the footer.

![](../assets/screenshots/btown-10-area.jpg)

## 18. FAQ
Split: headline left, `<details>` list right with serif questions and a + that rotates to × and fills with the gradient when open. Five questions that remove objections (files, turnaround, price finality, delivery, design help).

![](../assets/screenshots/eda-12-faq.jpg)

## 19. Final CTA
Dark, centred, giant serif headline with one accent turn, a lede, primary and light ghost buttons, radial glow rising from the bottom. Then the footer in the same ink.

![](../assets/screenshots/eda-13-final.jpg)
![](../assets/screenshots/btown-12-final.jpg)

## 20. Footer
Brand mark and name, one line of contact and hours, copyright, then a plain-text service-area sentence for SEO. Nightingale uses a giant wordmark above three columns (Write, Follow, Hours).

![](../assets/screenshots/nightingale-12-footer.jpg)

## Typical page orders

**Service sold on taste (Nightingale):** hero → planner band → manifesto → marquee → love notes → gallery → behind the scenes → footer.

**High-ticket offer (EDA):** hero → marquee → who it's for → comparison → founder story → what we build → timeline → love notes → value stack → guarantee → FAQ → final CTA → footer.

**Product / shop (B-Town):** hero → brands row → instant quote → product gallery → why us → process modules → love notes → what we do flip cards → service area → FAQ → final CTA → footer.
