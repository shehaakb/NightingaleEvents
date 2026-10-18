# Design system

The shared tokens, type scale and components. Copy the base, then swap palette and faces per client.

## Tokens by site

| Token | Nightingale | EDA | B-Town |
|---|---|---|---|
| paper | #faf6ee (ivory) | #fbf3ea | #fffdf6 |
| paper-2 | #f3eee3 | #f5e4d7 | #fff6d6 |
| ink | #45422c (moss deep) | #2b1418 | #1f1b14 |
| ink-soft | #6d6650 | #6e5054 | #66604f |
| primary | #5d593c moss | gradient #ff6a2b→#ff4f8b | #f2c230 yellow |
| accent | #ab6a6a rosewood | #ff4f8b pink | #3d6eeb blue |
| secondary | #beb06c linden, #d29e9e blush | #ffc9d6 blush | #b7e3d1 mint |
| display | Instrument Serif 400 | Instrument Serif 400 | Bricolage Grotesque 800 |
| body | Hanken Grotesk | Hanken Grotesk | DM Sans |
| radius | 20 px | 22 px | 22–28 px |
| ease | cubic-bezier(.2,.7,.1,1) | same | same |

Rules for choosing new ones:
- Paper is always warm. Pick it by tinting white 2 to 4 percent toward the primary.
- Ink is the primary's hue pushed almost to black, never neutral grey-black.
- Lines are ink at 14 percent alpha.
- Pick one accent for kickers and focus states that is *not* the primary, so the primary stays special.

## Base CSS

```css
:root{
  --paper:#fbf3ea; --paper-2:#f5e4d7; --ink:#2b1418; --ink-soft:#6e5054; --line:rgba(43,20,24,.14);
  --accent:#ff4f8b; --primary:#ff6a2b; --grad:linear-gradient(100deg,var(--primary),var(--accent));
  --serif:"Instrument Serif",serif; --sans:"Hanken Grotesk",system-ui,sans-serif;
  --wrap:1200px; --radius:22px; --ease:cubic-bezier(.2,.7,.1,1);
}
body{margin:0;background:var(--paper);color:var(--ink);font:17px/1.6 var(--sans);-webkit-font-smoothing:antialiased;overflow-x:hidden}
h1,h2,h3{margin:0;font-weight:400}      /* 800 for the grotesque sites */
.wrap{max-width:var(--wrap);margin:0 auto;padding:0 28px}
.section{padding:clamp(80px,12vw,150px) 0;position:relative}

/* grain: the one thing every site has */
.grain{position:fixed;inset:0;z-index:100;pointer-events:none;opacity:.07;
  background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='160' height='160'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.9' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E")}
```

## Type scale and the section opener

```css
.kicker{display:inline-flex;align-items:center;gap:12px;margin:0 0 22px;font-size:13px;font-weight:600;letter-spacing:.16em;text-transform:uppercase;color:var(--accent)}
.kicker::before{content:"";width:28px;height:1px;background:currentColor}
.h2{font-family:var(--serif);font-size:clamp(40px,6vw,78px);line-height:1.02;letter-spacing:-.015em;max-width:16ch}
.h2 em{color:var(--accent)}                       /* serif sites: italic accent */
/* grotesque sites: marker highlight instead */
.h2 em{font-style:normal;background:linear-gradient(transparent 58%,var(--primary) 58%,var(--primary) 94%,transparent 94%);padding:0 .06em}
.lede{font-size:clamp(17px,1.6vw,20px);color:var(--ink-soft);max-width:52ch;margin-top:26px}
.grad-text{background:var(--grad);-webkit-background-clip:text;background-clip:text;color:transparent}
```

Hero titles go bigger: `clamp(40px,4.6vw,66px)` on a split hero, `clamp(44px,7.4vw,112px)` on a centred one. Keep `max-width` at 12 to 20 characters so lines break on purpose.

## Buttons

```css
.btn{display:inline-flex;align-items:center;justify-content:center;gap:8px;padding:18px 30px;border-radius:999px;font-weight:600;font-size:16px;text-decoration:none;border:1px solid transparent;cursor:pointer;transition:transform .35s var(--ease),box-shadow .35s var(--ease),background .35s;white-space:nowrap}
.btn:hover{transform:translateY(-2px)}
.btn-grad{background:var(--grad);color:#fff;background-size:160% 100%;box-shadow:0 10px 30px -10px rgba(255,79,139,.65)}
.btn-grad:hover{background-position:100% 0}
.btn-ink{background:var(--ink);color:var(--paper)}
.btn-ghost{border-color:var(--line);background:rgba(255,255,255,.4);backdrop-filter:blur(6px)}
.btn-sm{padding:11px 20px;font-size:14px}
```

On a solid-primary site (B-Town) the primary button is flat brand colour with ink text and a coloured shadow.

## Floating pill nav

```css
.nav{position:fixed;top:16px;left:50%;transform:translateX(-50%);z-index:50;width:min(calc(100% - 32px),1160px);display:flex;align-items:center;justify-content:space-between;gap:20px;padding:10px 10px 10px 20px;border-radius:999px;background:rgba(251,243,234,.72);backdrop-filter:blur(14px) saturate(1.3);border:1px solid rgba(43,20,24,.08);transition:box-shadow .4s,background .4s}
.nav.scrolled{box-shadow:0 12px 40px -18px rgba(43,20,24,.35);background:rgba(251,243,234,.9)}
.brand-mark{width:40px;height:40px;border-radius:50%;display:grid;place-items:center;background:var(--grad);color:#fff;font-family:var(--serif);font-style:italic}
.nav-links a{font-size:14px;font-weight:500;color:var(--ink-soft);position:relative;text-decoration:none}
.nav-links a::after{content:"";position:absolute;left:0;bottom:-4px;height:1px;width:100%;background:var(--accent);transform:scaleX(0);transform-origin:right;transition:transform .4s var(--ease)}
.nav-links a:hover::after{transform:scaleX(1);transform-origin:left}
@media(max-width:900px){.nav-links{display:none}}
```

Nightingale uses a minimal variant: wordmark left, "Inquire" pill and "Menu" right, with a full-screen overlay menu of display-size links. Use that when the site has three or fewer destinations.

## Frames and label pills

```css
.frame{position:relative;overflow:hidden;border-radius:20px;display:flex;align-items:flex-end;padding:18px;background:var(--grad)}
.frame img,.frame video{position:absolute;inset:0;width:100%;height:100%;object-fit:cover}
.frame span{position:relative;font-size:12px;font-weight:600;letter-spacing:.1em;text-transform:uppercase;background:rgba(251,243,234,.9);padding:6px 12px;border-radius:999px}
.arch{aspect-ratio:3/4.2;border-radius:999px 999px 26px 26px}   /* arch-top variant */
```

Staggered 12-column gallery (both Nightingale and EDA): `grid-template-columns:repeat(12,1fr);grid-auto-rows:90px;gap:18px`, then place frames with explicit `grid-area`. Collapse to two columns under 640 px.

## Reveal, marquee, count-up

```js
// fade-up reveals with sibling stagger; native scroll, nothing pinned
const io=new IntersectionObserver(es=>es.forEach(e=>{
  if(!e.isIntersecting)return;
  const sib=[...e.target.parentElement.children].filter(c=>c.classList.contains('reveal'));
  e.target.style.transitionDelay=`${Math.min(sib.indexOf(e.target),6)*70}ms`;
  e.target.classList.add('in');io.unobserve(e.target);
}),{threshold:.12,rootMargin:'0px 0px -6% 0px'});
document.querySelectorAll('.reveal').forEach(el=>io.observe(el));
```
```css
.reveal{opacity:0;transform:translateY(22px);transition:opacity .9s var(--ease),transform .9s var(--ease)}
.reveal.in{opacity:1;transform:none}
.marquee{background:var(--ink);color:var(--paper);overflow:hidden;padding:22px 0;transform:rotate(-1.2deg);margin:0 -2vw;width:104vw}
.marquee-track{display:flex;gap:34px;width:max-content;animation:marquee 38s linear infinite}
.marquee span{font-family:var(--serif);font-style:italic;font-size:clamp(26px,3vw,40px);white-space:nowrap}
@keyframes marquee{to{transform:translateX(-50%)}}
@media(prefers-reduced-motion:reduce){.reveal{opacity:1;transform:none}.marquee-track{animation:none}}
```

Duplicate the marquee content once so the 50 percent translate loops seamlessly. Nightingale's marquee is unrotated and bordered; EDA and B-Town rotate it 1.2 degrees. Drop the marquee entirely when the owner finds it busy (B-Town did).

## Dark glow section

```css
.stack{background:var(--ink);color:var(--paper);overflow:hidden;position:relative}
.stack::before{content:"";position:absolute;width:70vw;height:70vw;left:-20vw;top:-10vw;border-radius:50%;background:radial-gradient(circle,rgba(255,106,43,.35),transparent 60%);pointer-events:none}
.stack::after{content:"";position:absolute;width:60vw;height:60vw;right:-20vw;bottom:-20vw;border-radius:50%;background:radial-gradient(circle,rgba(255,79,139,.32),transparent 60%);pointer-events:none}
```

## Accessibility and motion defaults
- Focus rings: 3 px solid accent, 3 px offset, on every button, chip and summary.
- `prefers-reduced-motion`: reveals shown, marquees and bobbing stopped, hero animation replaced by a finished frame.
- Alt text on every real photo; decorative SVG gets `aria-hidden`.
- Hover-only interactions get a touch fallback (`@media(hover:none)`).
