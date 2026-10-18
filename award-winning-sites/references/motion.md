# Motion

The hero carries the site, so it gets the one big animated idea. Everything below gets reveals and at most one small delight. All motion respects `prefers-reduced-motion` by showing the finished state.

## Choosing the hero mechanic

| If the business is… | Use | Shipped on |
|---|---|---|
| Sold on atmosphere (decor, venues, florals, photography) | **Curtain reveal**: a soft layer parts on scroll to uncover a real video of the work | Nightingale |
| An offer or a person (coaching, consulting, a founder brand) | **Framed proof**: animated drape at the top, arch-framed photo, floating stat badges, proof bar with count-up | EDA |
| A physical product or a shop | **The product doing its thing**: the actual machine or object, large, performing in a loop, with claim bubbles around it; a rotating headline naming what it makes | B-Town |

If the hero could be reused for a different business by swapping the logo, it is not finished.

## 1. Curtain reveal (Nightingale)

A 200vh hero with a sticky 100svh stage. A WebGL silk layer (Three.js) sits over a fixed `<video>`. Scroll progress drives the silk apart and fades the hero copy between 50 and 88 percent progress. The video is loaded 600 ms after `load` so it never competes with first paint.

```js
// simplified from hero-video.js
const progress = clamp(-hero.getBoundingClientRect().top / (hero.offsetHeight - innerHeight), 0, 1);
copy.style.opacity = clamp(1 - (progress - .5) / .38, 0, 1);
video.style.opacity = clamp(progress / .06, 0, 1);
video.style.transform = `translate3d(0, ${stage.getBoundingClientRect().top}px, 0)`;
```

A preloader counts 00→100 in the display face and slides away; the nav and copy then stagger in with GSAP (`autoAlpha`, 16 px rise, .8 s). Lighter alternative without WebGL: two CSS layers with a `mask-image` radial that grows with scroll.

## 2. Framed proof (EDA)

- **Drape:** an inline SVG at the top of the hero with three `<path>` layers, each with an `<animate attributeName="d">` loop of 8 to 11 s between two curve states. Gradient fills in brand colours, thin white strokes at 28 percent for sheen.
- **Arch photo:** `border-radius:999px 999px 26px 26px`, gradient fallback until the image loads, label pill inside.
- **Badges:** absolutely positioned cards with a big serif number and a caption; `animation: bob 6s ease-in-out infinite` with staggered negative delays.
- **Load-in:** `.load{animation:rise 1.1s var(--ease) forwards;animation-delay:calc(var(--d)*.12s + .15s)}` with `--d` set per element.
- **Count-up:** cubic-eased number tween over 1.6 s starting 600 ms after load.

## 3. The product doing its thing (B-Town)

**Rotating headline.** "We print the ___". The blank is a block-level, overflow-hidden line; words are absolutely positioned and centred. Outgoing word slides fully up and out (0.4 s, ease-in), *then* the next slides up and in (0.5 s, ease-out). No overlap, no horizontal movement, no rotation. 2.6 s per word. Give the clip box ~1.3em height so tall glyphs and ligatures are not cut.

```js
setInterval(()=>{
  const cur=rot.querySelector('span:not(.out)'); i=(i+1)%words.length;
  cur.classList.add('out');
  setTimeout(()=>{cur.remove();const n=document.createElement('span');n.textContent=words[i];n.className='in';rot.appendChild(n);},420);
},2600);
```
```css
.rot{display:block;position:relative;height:1.3em;overflow:hidden;text-align:center}
.rot span{position:absolute;left:50%;top:.06em;transform:translateX(-50%)}
.rot span.out{animation:wout .4s cubic-bezier(.5,0,.75,0) forwards}
.rot span.in{animation:win .5s cubic-bezier(.16,1,.3,1) both}
@keyframes wout{to{opacity:0;transform:translate(-50%,-100%)}}
@keyframes win{from{opacity:0;transform:translate(-50%,100%)}}
```

**Printer loop.** The client's machine photo, background removed and duotoned to the brand colour (percentile-stretch luminance, map dark→deep, mid→primary, light→pale), at near full page width. A clipped "feed" box starts at the paper slot; each sign is a transparent PNG that translates from fully above the slot to hanging in front of the basket, holds, then drops and fades. 1.5 s per sign, constant loop, paused only when fully off screen. The owner explicitly asked for *no* scroll-scrubbing so visitors always see the whole set.

```js
const CYCLE=1500; let t=0,last=null;
function render(){const total=t/CYCLE,idx=Math.floor(total)%prints.length,p=total%1;
  prints.forEach((el,i)=>{ if(i!==idx){el.style.opacity=0;return;} el.style.opacity=1; const H=el.offsetHeight;
    if(p<.55) el.style.transform=`translateY(${(p/.55-1)*H}px)`;          // feeding out
    else if(p<.8) el.style.transform='translateY(0)';                      // hold
    else {const q=1-Math.pow(1-(p-.8)/.2,3); el.style.transform=`translateY(${q*160}px) rotate(${q*-5}deg)`; el.style.opacity=1-q;} });
}
```

**Claim bubbles.** Five pills with an icon circle, a bold claim and a one-line proof, bobbing with staggered delays, positioned around the object. On mobile keep four and shrink them.

## Small delights for inner sections

- Flip cards: `perspective:1200px`, `.7s cubic-bezier(.4,.2,.2,1)` rotateY, backface hidden, stacked faces under `@media(hover:none)`.
- Hover lift: `translateY(-4px) rotate(-.4deg)` with a soft shadow on list cards.
- Underline grow on nav links from right to left on hover.
- `<details>` plus icon rotating 45° and filling with the gradient.
- Sticky left intro in split sections.
- Label pill text swap: fade and 6 px drop over 250 ms when the printed item changes.

## Things we tried and removed
- Scroll-scrubbed hero loops (visitors never see every item). Replaced by a timed loop.
- Rotating headline words that also changed container width (read as a sideways swipe). Fixed-line, vertical-only swap instead.
- Two words visible during a swap (looked laggy). Sequence out then in.
- A pulsing "live" dot in the eyebrow. Owner called it out as noise.
- A drape and an arch on a product site. Too soft for a physical product.
