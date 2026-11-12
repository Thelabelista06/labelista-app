# The Labelista — App (free PWA + APK)

Free Android app for https://www.thelabelista.com — a Trusted Web Activity
wrapping the live Shopify store. No Play Console account needed for the APK.

- App source: `free-apk/` (TWA manifest, PWA manifest, icons)
- Build: GitHub Actions, `.github/workflows/build-apk.yml`
  — Actions tab → "Build Labelista APK (free)" → Run workflow → download
  the `labelista-debug-apk` artifact.
- Icons are stored as `assets/*.png.b64` (base64 text) and decoded to PNG
  by the workflow, so they can be pushed through the GitHub connector.
- Play Store pack (for later, $25): see the `workspace/labelista-app/`
  folder in Muse, not this repo.
