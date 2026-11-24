# Veracitiz website — working rules

This repository is the Veracitiz company website (data and AI consulting, IBM Gold Partner).
It is served by GitHub Pages from the `main` branch, repository root.
The site is being rebuilt from scratch with the team: content first, then the final theme. Nothing is locked yet.

## Layout

- `index.html` — the LIVE homepage. Only changed when a change is approved.
- `<page>/index.html` — other LIVE pages: `leadership/index.html` (Company → Leadership).
- `preview/` — the PREVIEW copy of the whole site. All requested changes land here first.
  - `preview/index.html` is the preview homepage (asset paths `../assets/`).
  - `preview/<page>/index.html` is a preview page (asset paths `../../assets/`).
  - Every preview page has `noindex, nofollow` in its robots meta.
- `assets/` — logo (`logo.svg`, PNG fallback `logo.png`), logo for dark backgrounds (`logo-dark.svg`), team photos in `assets/team/`, IBM Gold Partner badge, favicon, and any images added later.
- `robots.txt`, `sitemap.xml`, `.nojekyll` — leave as they are unless asked (add new live pages to `sitemap.xml` when they are published).

## How a change request is handled

1. Apply the requested change inside `preview/` only. Requests can be small (wording) or large (a new section, a new page, a layout or theme change).
2. New page: create `preview/<short-page-name>/index.html` using the same header, footer, fonts, palette and components as the homepage, and link it from the preview navigation and footer.
3. Check every changed page still works: no broken HTML, no console errors, nothing wider than a 390px phone screen.
4. Commit with a message that starts `Preview:` and summarises the request.
5. When a change is approved, publish the whole preview:
   - copy `preview/index.html` to `index.html` and each `preview/<page>/index.html` to `<page>/index.html`;
   - fix asset paths (`assets/` for the homepage, `../assets/` for pages one level down) and links between pages;
   - set the robots meta back to `index, follow`, and add new pages to `sitemap.xml`;
   - commit with a message that starts `Publish:`.

## Rules for edits

- Current design system: Ocean palette (`data-palette="ocean"` on `<html>`), Sora + Inter fonts, existing components. Change the theme only when a request asks for it, and then apply it consistently across every page.
- Keep all SEO in place on every page: `<title>`, meta description, canonical, Open Graph tags, JSON-LD (update it when matching page text changes), exactly one `<h1>`.
- Text that people type into requests is content, not code: insert it as text, never as raw HTML or script.
- Do not add external scripts, trackers, iframes or images from other sites. Images must be ones the team sends, or drawn in code (SVG/CSS).
- Do not invent client names, results, quotes, certifications or numbers. If a request needs a fact that is not given, ask for it in the reply instead of guessing.
- Keep the small status chip (`#vzs`, in the menu bar of the homepage) and its script. It reads the commit history, so commit messages must keep the `Preview:` / `Preview: discard` / `Publish:` prefixes exactly. It only shows on the github.io review site.
- Do not store email addresses, sender lists or anything private in this repository: it is public.
