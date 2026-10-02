# Mum's House

Estate inventory and allocation. Static site: `public/index.html`, full photos in `public/photos/`, 800px copies in `public/thumbs/`.
Decisions sync through Firebase Realtime Database (`mumshouse/...`).

## Deploy (Cloudflare Pages)

- Build command: none
- Build output directory: `public`

## Notes

- Photos have had GPS EXIF removed. Strip it from any new photo before adding.
- New photo? Add a thumbnail at the same path under `public/thumbs/`:
  `convert in.jpeg -auto-orient -resize '800x800>' -strip -quality 72 -interlace JPEG out.jpeg`

## Security

- The site signs in to Firebase anonymously. Database rules live in `database.rules.json`.
  Paste them into Firebase console → Realtime Database → Rules.
- The PIN at `mumshouse/config/pin` is never sent to the browser. A guess is written to
  `mumshouse/unlocks/<uid>` and the rules only accept it if it matches.
- Anonymous sign-in lets anyone who can load the page read the data. Cloudflare Access
  on the Pages project is what limits who can load the page.
