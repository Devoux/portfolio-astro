# Portfolio (Astro)

## Quick start

1. Install dependencies:
   - `npm install`

2. Run the dev server:
   - `npm run dev`

## Build

- `npm run build`
- Output goes to `dist/`

## Deploy (Firebase Hosting)

1. Build the site:
   - `npm run build`

2. Deploy:
   - `firebase deploy --only hosting`

## Firebase Hosting Setup (One-time)

1. Initialize Hosting:
   - `firebase init hosting`
   - Public directory: `dist`
   - SPA rewrite: `N`

2. Login if needed:
   - `firebase login`

3. Set project (if multiple):
   - `firebase use <project-id>`

## Local Hosting Preview

- `firebase emulators:start --only hosting`

## Media Embeds

- Shared styles live in `src/styles/global.css` (e.g., `.project-media`, `.project-media-image`, `.project-video`, `.project-video--portrait`, `.media-carousel`, `.media-panel`, `.project-pdf`).
- Carousels are implemented with inline scripts on the relevant project page.
- The Firebase emulator does not support byte-range requests, so video scrubbing may not work locally. Test on the deployed site or use a local static server that supports ranges.

## Custom Domain (Cloudflare)

- Add domain in Firebase Console → Hosting → Add custom domain.
- Add the TXT record for domain verification in Cloudflare DNS.
- Add the A/AAAA records Firebase provides and remove conflicting records.

## Caching

- HTML is configured to revalidate immediately via `firebase.json` headers (`Cache-Control: public, max-age=0, must-revalidate`).
- After changing caching headers, rebuild and redeploy.

## Structure

- `src/pages/index.astro`: main bio page
- `src/pages/projects/index.astro`: project list
- `src/pages/projects/*.astro`: individual project pages
- `src/pages/contact.astro`: contact page
- `src/pages/resume.astro`: resume page
- `public/resume.pdf`: replace with your real resume PDF
- `public/`: put images and media here for easy linking

## Replace content

- Update text in the page files under `src/pages/`.
- Replace placeholder project descriptions and media.
- Swap `public/resume.pdf` with your real resume file (same name).
