# Dungeon PvP PoC v0.9 — Mobile / PWA

## v0.9 changes
- Mobile BUILD layout is now vertically scrollable instead of being clipped by a fixed desktop-height grid.
- Board height follows its 12:10 tile aspect ratio on phones; it no longer expands to fill the remaining viewport.
- Piece palette becomes a compact 3-column (2-column on very narrow phones) touch layout.
- Vertical scrolling is allowed during BUILD, while RAID keeps `touch-action: none` so swipes remain game input.
- BUILD placement uses click/tap rather than pointer-down so scrolling the board does not accidentally paint at touch start.
- RAID canvas resolution adapts to portrait/landscape aspect while keeping low-resolution pixel rendering.
- Safe-area padding added for Android/iOS display cutouts.
- PWA manifest + service worker added. Once hosted over HTTPS (for example GitHub Pages), the game can be added to the phone home screen and cached for offline use.
- GitHub Pages deployment workflow is included at `.github/workflows/pages.yml`.

## Why ChatGPT mobile downloads the HTML
The ChatGPT mobile client does not execute a sandbox HTML attachment inline like a hosted web page. A stable no-redownload experience therefore requires hosting the static files at an HTTPS URL. GitHub Pages is enough; no backend is required for this PoC.

## GitHub Pages quick deploy
1. Create or use a repository and put the contents of this folder at its repository root.
2. Push to the `main` branch.
3. In GitHub: Settings → Pages → Source, select **GitHub Actions** if it is not already selected.
4. Run or wait for `Deploy Dungeon PvP to GitHub Pages`.
5. Open the resulting Pages URL on Android/iPhone.
6. Browser menu → **Add to Home screen / Install app**. After the first load, the service worker caches the PoC.

No game backend is needed yet; this is a static HTML/JS PoC.
