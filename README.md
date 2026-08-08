<p align="center"><a href="https://loop.sv-academy.org"><img src="https://raw.githubusercontent.com/sva-admin/claude-skills/main/assets/sv-academy-512.png" width="96" alt="Silicon Valley Academy"/></a></p>

# animated-website

A landing page with real scroll animation, delivered as one self-contained HTML file you can open, host, or hand to a client.

> **Transparency**
>
> An independent SV Academy implementation, written from scratch. Credit below.

## Try it

Paste this into Claude Code:

```
Install the skill from https://github.com/sva-admin/animated-website, then build me a landing page for a Bangkok sourdough bakery that takes weekend preorders.
```

## What comes back

One `.html` file, every style and script inline, no CDN and no build step. Scroll reveals with a single IntersectionObserver, staggered cards, at most two parallax layers, hover states that behave on touch, and a type and color system defined as tokens instead of scattered hex codes.

The guardrails are the point. The skill refuses to invent testimonials or logos you didn't supply, holds the page to three motion ideas total, animates only `transform` and `opacity`, keeps the copy readable with JavaScript disabled, and collapses every entrance to its final state under `prefers-reduced-motion`. It ships against a checklist: 360px wide, keyboard reachable, contrast at 4.5:1, no layout shift as sections reveal.

## Learn it free, step by step

[Landing page with motion](https://loop.sv-academy.org/articles/landing-page-with-motion)

## Credit

Inspired by the `animated-website` skill that circulates in the community "Claude Code Skills Bundle", published there with no author name and no license attached. This is an independent SV Academy implementation: the instructions here were authored fresh, and no text was carried over. If you wrote the original, open an issue and we will credit you by name in this section.

The SV Academy text in this repo is MIT licensed. See [LICENSE](LICENSE).

## More from Silicon Valley Academy

- All of our published skills: [github.com/sva-admin/claude-skills](https://github.com/sva-admin/claude-skills)
- Courses and free lessons: [sv-academy.org](https://sv-academy.org)
