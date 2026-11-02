# yahya-shihabe.pages.dev

Personal site for Yahya Shihabe, AI consultant in Sweden. One static page, bilingual
(English / Swedish), positioned at small Swedish businesses that lose enquiries and do
their admin by hand.

Live site: [yahya-shihabe.pages.dev](https://yahya-shihabe.pages.dev)

---

## What is on the page

| Section | English | Swedish |
|---|---|---|
| Hero | Outcome first: answers every enquiry, takes the admin off your desk | same |
| Selected work | Two live builds, public source | samma |
| Services | Four fixed-scope offers | fyra tjänster |
| How I work | Diagnose, scope, build, hand over | diagnos, omfattning, bygge, överlämning |
| About | Who, how, what you get | om mig |
| Contact + booking | Cal.com inline embed | boka |

A language toggle (EN / SV) swaps the sections, nav labels, CTAs and the page metadata.
Swedish is also reachable directly at `/?lang=sv`, which the canonical and `hreflang` tags
point at.

## Files

```
index.html      the whole site: markup, styles, i18n, Cal.com embed
404.html        error page
robots.txt      allow all, absolute sitemap URL
sitemap.xml     both language URLs, with hreflang alternates
og.png          1200x630 social card
favicon.svg     YS monogram
assets/         portrait (yahya.jpg) and the Hermes Agent lockup
```

No build step, no framework, no runtime dependencies. Styling is Tailwind (CDN) with
Fraunces and Inter from Google Fonts, plus a small block of custom CSS in `index.html`.

## Featured projects

| Project | Live | Source |
|---|---|---|
| AI Receptionist & Lead Capture | [demo](https://ai-receptionist-demo.yahya-shehabi01.workers.dev) | [repo](https://github.com/Yahya-Shihabe/ai-receptionist-demo) |
| Agent Workflow Playground | [demo](https://agent-workflow-playground.yahya-shehabi01.workers.dev) | [repo](https://github.com/Yahya-Shihabe/agent-workflow-playground) |

Card screenshots are loaded from each repo's `docs/screenshots/` directory.

Vox (macOS dictation) and Brains (agent workspace) are mentioned in a short note. Neither
is public, so neither is presented as proof and neither has a link.

## Local development

```bash
python3 -m http.server 8000     # a static server, so the Cal.com embed can load
```

## Deployment

Cloudflare Pages, auto-deployed from `main`.

```bash
git add -A
git commit -m "update: reposition as AI consultant"
git push origin main
```

Live within about a minute.

## Checks that should pass

1. `GET /` returns 200 `text/html`; the English page renders with no console errors.
2. `GET /robots.txt` returns 200 `text/plain`; `/sitemap.xml` returns 200 `application/xml`.
3. `GET /og.png` returns 200 `image/png` and the artwork is legible at 1200x630.
4. An unknown path returns 404 (serves `404.html`, not the homepage).
5. `SV` toggle: Swedish sections show, English hides, `html lang` becomes `sv`, the title
   and description swap, and every booking CTA lands on the Cal.com widget.
6. At 390px width there is no horizontal overflow and the sticky "Book" bar is visible.
7. External links resolve: both demo sites, both demo repos, the GitHub profile, Cal.com.

## License

MIT
