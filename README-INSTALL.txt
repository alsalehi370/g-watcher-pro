# G Watcher PRO — iPhone PWA package

This package adapts your supplied G Watcher PRO HTML dashboard for installation on an iPhone home screen. It keeps the existing quote source and calculations, adds an installable PWA manifest, iPhone home-screen icon metadata, a service worker for the app shell, a compact mobile layout, and remembers the USD/OMR rate on that device.

## Install on iPhone (no App Store / no Mac)

1. Upload the **contents** of this folder to an HTTPS static host (for example, a private GitHub Pages repository or a static hosting service). The host must serve `index.html` at the site root.
2. Open the HTTPS site address in **Safari** on your iPhone.
3. Tap **Share** → **Add to Home Screen** → **Add**.
4. Launch **G Watcher PRO** from its new home-screen icon.

A website must be served over HTTPS for service workers/PWA offline shell support. A PWA is not a signed native iOS app; it runs in Safari's installed web-app mode and does not require App Store registration or an Apple Developer membership.

## Local preview on Windows

Open PowerShell in this folder and run:

```powershell
py -m http.server 8000
```

On your PC, visit `http://localhost:8000`. This is for preview only. For iPhone installation, deploy to HTTPS; the phone must be able to reach the hosted site.

## Important live-data note

The original dashboard requests XAUUSD and DXY from `https://biquote.io/api` every 5 seconds. This package deliberately does **not** cache API responses: live quotes require internet access and the API must remain available and permit requests from the deployed site. Offline mode only keeps the app shell available; it cannot provide live prices. The quote provider's reliability, terms, and CORS policy are external dependencies.

## Files

- `index.html` — your adapted dashboard
- `manifest.webmanifest` — install name, display mode, colors, icons
- `service-worker.js` — caches the app shell, never live quotes
- `icons/` — app and iPhone home-screen icons
