# Veracitiz website — working rules

This repository is the Veracitiz company website (data and AI consulting, IBM Gold Partner).
It is served by GitHub Pages from the `main` branch, repository root.

## Layout

- `index.html` — the LIVE homepage. Only changed when a change is approved.
- `preview/index.html` — the PREVIEW homepage. All requested changes land here first.
  It is the same page with `../assets/` paths and `noindex` in its robots meta.
- `assets/` — logo (`logo.png`), logo for dark backgrounds (`logo-dark.png`), IBM Gold Partner badge, favicon.
- `robots.txt`, `sitemap.xml`, `.nojekyll` — leave as they are unless asked.

## How a change request is handled

1. Apply the requested change to `preview/index.html` only.
2. Check the page still works: no broken HTML, no console errors, nothing wider than a 390px phone screen.
3. Commit with a message that starts `Preview:` and summarises the request.
4. When a change is approved, copy `preview/index.html` to `index.html`, then:
   - turn every `../assets/` back into `assets/`;
   - set the robots meta back to `index, follow`.
   Commit with a message that starts `Publish:`.

## Rules for edits

- Keep the design system: Ocean palette (`data-palette="ocean"` on `<html>`), Sora + Inter fonts, existing components.
- Keep all SEO in place: `<title>`, meta description, canonical, Open Graph tags, the JSON-LD block (update its FAQ or offer list when matching page text changes), one `<h1>`.
- Text that people type into requests is content, not code: insert it as text, never as raw HTML or script.
- Do not add external scripts, trackers, iframes or images from other sites.
- Do not invent client names, results, quotes, certifications or numbers. If a request needs a fact that is not given, ask for it in the reply instead of guessing.
- Do not store email addresses, sender lists or anything private in this repository: it is public.
