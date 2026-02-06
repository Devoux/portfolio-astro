# Portfolio Project (Astro) — AGENTS.md

## Purpose
Static portfolio site for Alder Nadon. Bio + project detail pages + resume/contact. Built for easy content updates and media embedding.

## Tech Stack
- Astro (static site)
- Vanilla HTML/CSS (no framework UI)
- Python (only for external terrain generator project files; not part of site runtime)

## Project Structure (site)
- `portfolio-astro/` — main Astro site
  - `src/pages/index.astro` — bio + current focus + projects grid
  - `src/pages/projects/*.astro` — individual project pages (What/How/Why + skills)
  - `src/pages/resume.astro` — resume download + embedded PDF viewer
  - `src/pages/contact.astro` — contact info
  - `src/layouts/BaseLayout.astro` — global layout + nav + footer
  - `src/styles/global.css` — all styling (theme, layout, components)
  - `public/` — static assets (images, pdf, video)
    - `public/projects/` — project thumbnails
    - `public/resume.pdf` — downloadable resume

## Design Notes
- Dark graphite + amber palette defined in `:root` CSS vars.
- Project cards are fully clickable links with hover highlights.
- Footer is a bottom-anchored banner with middot separators.
- Resume PDF embedded via `<object>` (browser-native viewer).
- Media embeds use shared classes in `src/styles/global.css` (`.project-media`, `.project-media-image`, `.project-video`, `.project-video--portrait`, `.media-carousel`, `.media-panel`, `.project-pdf`).
- Carousels are implemented with inline scripts on the project pages that include them.

## Running Locally
```bash
cd portfolio-astro
npm install
npm run dev
```

## Build & Deploy (Firebase Hosting)
```bash
cd portfolio-astro
npm run build
firebase deploy --only hosting
```

## Firebase Hosting Notes
- Firebase config lives in `portfolio-astro/firebase.json` and `.firebaserc`.
- Hosting is configured for Astro's build output (`dist/`).
- Custom domains are set in the Firebase Console; DNS records are managed in Cloudflare.
- Use `firebase emulators:start --only hosting` for local Hosting preview.
- HTML responses are set to revalidate immediately via `firebase.json` headers to avoid stale custom-domain caches.
- Firebase emulator does not support byte-range requests, so video scrubbing may fail locally; test on deployed Hosting or a range-capable local server.

## Content Workflow
- Update copy in the relevant `.astro` page file.
- Add media to `public/` and link with `/filename.ext`.
- Project templates follow: Skills → What → How → Why → Team → Media.

## Additional Repo Content
- `terrain-applications/` contains Python PyQt terrain generator code (not required for site).
- `Portfolio (2-5-26).html` is the original Google Sites export (reference only).
