---
name: animated-website
description: Build a production-ready animated landing page as one self-contained HTML file. Scroll reveals, parallax depth, hover states, a real type and color system, plus reduced-motion and performance guardrails. Trigger on "build me a landing page", "animated website", "marketing page for", "product page with animation", "scroll animation site", "one-page site", "landing page with motion", or any request for a polished web page where the motion is part of the pitch.
---

# Animated Landing Page

One file. Real motion. Opens with a double click, no build step, no CDN.

## The deliverable

A single `.html` file with every style and script inline. No external requests at runtime. Default to a system font stack; only reach for a webfont if the brand needs a specific display face, and then embed it as a base64 `@font-face` so the file still works offline.

## Step 1: get four answers

Ask all four in one message. Don't start building until you have them.

1. Who lands on this page, and what do they already believe about the problem?
2. What is the one action the page has to produce, and what URL does it point at?
3. What single sentence would make that person take the action?
4. Brand inputs: name, any hex colors you must honor, any logo or photos sitting in the working folder.

If the answer is "you pick", pick. Then state your picks in one line before you write code, so the user can correct you cheaply.

## Step 2: choose the spine

Use five to eight modules, in this order. Drop any module you cannot fill with something true.

- **Hook.** Headline, one-sentence subhead, primary button, one visual that moves.
- **Proof.** Logos, hard numbers, or two short quotes with real names attached. If none were supplied, cut this module. Do not manufacture it.
- **Value.** Three or four cards, each a benefit in the reader's words, not a feature in yours.
- **Mechanism.** Three steps showing how it actually works. This is where skeptics get converted.
- **Offer.** Pricing cards or one clear offer box. Name the price or name why there isn't one.
- **Objections.** An accordion answering the four questions a doubtful reader actually asks, not the four that flatter the product.
- **Close.** The same button as the hook, word for word.
- **Footer.** Contact, legal, socials.

Hard rule: never invent testimonials, client logos, or statistics. Missing input means a missing module, not a placeholder.

## Motion doctrine

Five rules. They are not negotiable, because breaking them is exactly what makes an animated page feel cheap.

1. **Animate `transform` and `opacity` only.** Anything that touches layout (`top`, `height`, `margin`, `width`) runs on the main thread and stutters on a mid-range phone.
2. **Three motion ideas, maximum.** Pick three, use them consistently, repeat them. A page with nine different entrance effects reads as a demo, not a product.
3. **Entrances fire once.** Unobserve the element after it reveals. Content that re-animates every time it scrolls past is nauseating on the second pass.
4. **Respect `prefers-reduced-motion: reduce`.** Under that query, every entrance collapses to its final state instantly, parallax layers freeze, and counters print their final number. The still version must look finished, not broken.
5. **Nothing important waits on motion.** Put an inline script in `<head>` that adds a `js` class to `<html>`, and scope every hidden-until-revealed rule to `.js`. If the script never runs, the page is simply a static page that reads correctly.

## The motion kit

Concrete primitives. Reach for these before inventing anything.

**Reveal on enter.** One `IntersectionObserver` for the whole page, `threshold: 0.15`, `rootMargin: "0px 0px -10% 0px"`. On intersect, add a class and unobserve. Transition `opacity .6s cubic-bezier(.16, 1, .3, 1)` and `transform .6s cubic-bezier(.16, 1, .3, 1)`, starting from `translateY(24px)`.

**Stagger.** Set `style="--i: 0"`, `1`, `2` on siblings and use `transition-delay: calc(var(--i) * 70ms)`. Cap the index at 6 so the last card in a long list never feels abandoned.

**Parallax depth.** Prefer CSS scroll-driven animation (`animation-timeline: view()`) and let unsupported browsers show the static layout. If you need a JS fallback, use one `requestAnimationFrame` loop that writes one transform per frame, never a handler per element. Two layers maximum, 80px of travel maximum.

**Counters.** Start only when the stat scrolls into view. Ease out over about 1.2s. Reserve the digit width up front (`font-variant-numeric: tabular-nums`) so the layout doesn't twitch as the number climbs.

**Hover.** 150ms, `translateY(-2px)` plus one shadow step. Wrap it in `@media (hover: hover)` so touch devices don't get stuck in a hover state. Never put information in a hover-only state.

**Sticky moments.** Use `position: sticky` for pinned headlines and section headers. Never hijack the scrollbar with a JS scroll lock.

**Background.** One slow gradient or blob drift, 20s or longer, or nothing at all. Anything faster competes with the copy.

## Design constraints

- **Type.** Two families maximum. Hero at `clamp(2.5rem, 6vw, 4.5rem)`, body at 16px to 18px, line height 1.6, measure capped at 60ch to 72ch.
- **Color.** One brand color, one accent, one neutral ramp of four steps. Everything else is the neutral at reduced opacity. Define all of it as custom properties in `:root`.
- **Space.** An 8px base scale, and section padding at `clamp(4rem, 10vw, 8rem)`. Vertical rhythm is what separates expensive from generic.
- **Radius and shadow.** One radius token, two shadow steps. Not three, not per-component.
- **Contrast.** Body text at 4.5:1 or better against its background, button labels at 4.5:1 against their fill. Check the light gray subheads specifically, that's where it usually fails.
- **Mobile first.** Write the small layout, then add one breakpoint at 768px and at most one more at 1100px.

## Build order

Follow it. Skipping to motion first is how pages end up animated and unconvincing.

1. Tokens in `:root`: color, type scale, spacing, radius, shadow, easing.
2. Semantic HTML with the real copy and zero styling. Read it top to bottom. If it doesn't sell as plain text, fix the copy, not the CSS.
3. Layout and typography. The page should already look good, completely still.
4. Color, depth, imagery.
5. Motion, last.
6. Cut. Remove one section and one animation. The page usually gets better.

## Ship gate

Every line has to pass before you hand the file over.

- Opens from `file://` with the network off, and nothing is missing.
- Readable and clickable with JavaScript disabled.
- Under `prefers-reduced-motion: reduce`, the page is still and still looks deliberate.
- At 360px wide, nothing overflows sideways.
- Tab reaches every link and button, and the focus ring is visible on all of them.
- No layout shift as sections reveal, since reveals use `transform` only.
- One primary action, worded identically in the hook and the close.
- Zero lorem ipsum, zero invented customers, zero fake logos.

## Output

Write the file as `landing-<slug>.html` in the working directory.

Then report back three things and nothing more: the file path, the three motion ideas you committed to, and the one element you would A/B test first.
