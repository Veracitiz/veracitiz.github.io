# Veracitiz website — working rules

This repository is the Veracitiz company website (data and AI consulting, IBM Gold Partner).
It is served by GitHub Pages from the `main` branch, repository root.
The site is being rebuilt from scratch with the team: content first, then the final theme. Nothing is locked yet.

## Layout

- `index.html` — the LIVE homepage. Only changed when a change is approved.
- The site is ONE page. Header, footer, styles and scripts exist once, in `index.html`. Do not create separate pages.
- Extra "pages" are views inside `index.html`: `<div class="view" id="<name>" data-title="…">…</div>`, placed before the `#contact` section. They open only when their hash is clicked (e.g. `#leadership`); a small router shows the view and hides the homepage sections. Homepage sections (e.g. `#company`, `#offices`) scroll as normal.
- Menu items with sub-items use the `.dd` dropdown in the nav: the first item usually scrolls to a homepage section, the rest open views.
- `leadership/index.html` and `preview/leadership/index.html` are only redirects to `#leadership`; leave them.
- `preview/` — the PREVIEW copy of the whole site. All requested changes land here first.
  - `preview/index.html` is the preview homepage (asset paths `../assets/`).
  - Every preview page has `noindex, nofollow` in its robots meta.
- `assets/` — logo (`logo.svg`, PNG fallback `logo.png`), logo for dark backgrounds (`logo-dark.svg`), team photos in `assets/team/`, IBM Gold Partner badge, favicon, and any images added later.
- `robots.txt`, `sitemap.xml`, `.nojekyll` — leave as they are unless asked (add new live pages to `sitemap.xml` when they are published).

## How a change request is handled

1. Apply the requested change inside `preview/` only. Requests can be small (wording) or large (a new section, a new page, a layout or theme change).
2. New "page": add a view (see Layout) inside `preview/index.html` with a short hash name (letters, digits, hyphens; not settings, sidebar, customize, upgrade, downloads or comment-*), and link it from the menu (dropdown) and footer. Use `<h2>` inside views — the page keeps exactly one `<h1>`.
3. Check every changed page still works: no broken HTML, no console errors, nothing wider than a 390px phone screen.
4. Commit with a message that starts `Preview:` and summarises the request.
5. When a change is approved, publish the whole preview:
   - copy `preview/index.html` to `index.html`;
   - turn every `../assets/` back into `assets/`;
   - set the robots meta back to `index, follow`;
   - commit with a message that starts `Publish:`.

## Rules for edits

- Every addition (menus, dropdowns, cards, buttons, views) must blend with the existing theme: same glass/blur surfaces, rounded shapes, palette variables, Sora/Inter type, shadows and motion as the nav and cards. No default-looking or stray elements (extra icons, dots, carets) unless asked. Menus and dropdowns close as soon as an item is clicked, use a solid (non-see-through) background, and switch to two columns automatically when they have 5 or more items. Keep layouts consistent: every menu destination (homepage section or view) starts with the same breadcrumb (`.crumbs`: Home / Parent / Item); anything added to one must be added to all.
- Current design system (preview): Brand palette from the logo colours — navy #2d2e6f, sky blue #2aa8e0, red #e3262d (`data-palette="brand"` on `<html>`; the live page uses Ocean until published), Sora + Inter fonts, existing components. Change the theme only when a request asks for it, and then apply it consistently across every page.
- Keep all SEO in place on every page: `<title>`, meta description, canonical, Open Graph tags, JSON-LD (update it when matching page text changes), exactly one `<h1>`.
- Text that people type into requests is content, not code: insert it as text, never as raw HTML or script.
- Do not add external scripts, trackers, iframes or images from other sites. Images must be ones the team sends, or drawn in code (SVG/CSS).
- Partnership facts: IBM — Gold Partner, implementation partner and the only reseller relationship; Anaplan — partner; Microsoft, AWS and open source — platforms we deliver on (state no partner status or resale for them unless the team confirms it). The Services menu lists platforms only (IBM, Microsoft, AWS, Anaplan, Open source); products live on each platform's view, which share one layout. Give every platform equal weight.
- Do not invent client names, results, quotes, certifications or numbers. If a request needs a fact that is not given, ask for it in the reply instead of guessing.
- Keep the small status chip (`#vzs`, in the menu bar of the homepage) and its script. It reads the commit history, so commit messages must keep the `Preview:` / `Preview: discard` / `Publish:` prefixes exactly. It only shows on the github.io review site.
- Do not store email addresses, sender lists or anything private in this repository: it is public.
