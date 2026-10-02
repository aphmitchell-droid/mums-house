# Mum's House

Estate inventory and allocation. Static site: `public/index.html` plus `public/photos/`.
Decisions sync through Firebase Realtime Database (`mumshouse/...`).

## Deploy (Cloudflare Pages)

- Build command: none
- Build output directory: `public`

## Notes

- Photos have had GPS EXIF removed. Strip it from any new photo before adding.
- The PIN lives in Firebase at `mumshouse/config/pin`. Lock the database rules down before relying on it.
