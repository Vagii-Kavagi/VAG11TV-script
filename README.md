# VAG11TV-script

The page script for VAG11TV on Cobalt. The app is YouTube's open-source TV engine, Cobalt (built by
[TizenTubeCobalt](https://github.com/reisxd/TizenTubeCobalt)), and it loads this one file into
youtube.com/tv:

```
https://cdn.jsdelivr.net/gh/Vagii-Kavagi/VAG11TV-script@1/v.js
```

`@1` is the newest `1.x` tag, so the app only ever runs a version released here as a tag. A change
to `main` alone reaches nobody.

## What it does

- **Ad blocking:** the advert parts are taken out of YouTube's data before the page reads it
  (adverts in videos, the Home banner, Sponsored tiles, Shorts adverts).
- **Two entries in YouTube's Settings**, "Ad blocking" and "SponsorBlock", each opening a menu
  driven by the remote (Up/Down to move, OK or Left/Right to change, Back to close).
- **SponsorBlock:** segments reported by the SponsorBlock community are skipped, or offered with a
  skip button, per category. Only the first 4 characters of the SHA-256 of the video id are sent to
  sponsor.ajay.app.

Choices stay on the TV (localStorage). Nothing else is sent anywhere.

## Releasing

1. Change `v.js`, and its `version` near the top.
2. Commit, then tag with the same version, for example `git tag 1.0.1 && git push --tags`.
3. jsDelivr picks the new tag up within about 12 hours; the TV loads it on the app's next start.
