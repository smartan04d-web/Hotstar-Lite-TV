# Hotstar Lite TV (Unofficial)

Independent experimental Android TV WebView wrapper for JioHotstar. Not affiliated with or endorsed by JioHotstar or JioStar.

## Features
- Android 10+ (API 29), TV launcher banner
- Remote-focusable Home, Back, Reload, Browse, Ads Filter ON/OFF toolbar
- WebView fullscreen video callback
- Persistent optional third-party ad-domain filter (OFF by default)
- No background services or tracking SDKs

## Important limitations
- **Playback is not guaranteed**: JioHotstar may require its official app, DRM/Widevine, a supported browser, or device attestation. Android TV WebView availability varies.
- This filter only blocks a conservative list of third-party advertising hosts. It does **not** bypass DRM, subscriptions, server-side ads, mandatory ad countdowns, or provide automatic ad skipping.
- The website may not be fully navigable with a TV remote. A mouse/air mouse may be needed.
- Turn the filter OFF if playback, login, or page loading fails.
- No automated tests or real-device validation have been performed.

## Build APK via GitHub Actions
1. Create a new GitHub repository named `Hotstar-Lite-TV` with no auto-generated README.
2. Extract the ZIP and upload **contents** to repository root, including hidden `.github/workflows/build-apk.yml`.
3. Commit on `main` and open Actions > Build Hotstar Lite TV APK.
4. When successful, open the run > Artifacts > `Hotstar-Lite-TV-APK`.
5. Download and extract ZIP to obtain `app-debug.apk`.

## Install on Android TV
Transfer APK by USB or trusted transfer app, then enable **Install unknown apps** for the file manager and install. Menu names vary by TV. For security, disable this permission after installation.

## Local build
JDK 17, Android SDK 35, build-tools 35.0.0, Gradle 8.9. Run `gradle assembleDebug`.

## Package
`com.hotstartv.lite` — separate from LiteTube phone/TV apps.


## v2: Playback-safe filtering and optional Auto Skip
- **Safe Filter ON/OFF**: default OFF; blocks a short list of third-party advertising hosts, not Hotstar media/CDN/DRM hosts. Reloads page on toggle. May still disrupt site features; turn OFF if playback fails.
- **Auto Skip ON/OFF**: default OFF; checks once per second while foregrounded for an exact visible, enabled English `Skip Ad` button on a Hotstar page. It does not bypass mandatory countdowns, seek video, remove server-inserted ads, or guarantee any skips. The site may not expose such a button.
- Settings persist across restarts. No background service.
- GitHub Actions build: upload all files including `.github/workflows/build-apk.yml`, commit to main, download artifact from successful Actions run.
- This project is not endorsed by JioHotstar. DRM-protected playback and WebView support depend on TV device and service.
