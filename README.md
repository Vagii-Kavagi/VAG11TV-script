# VAG11TV-script

The page script for VAG11TV on Cobalt. The app is YouTube's open-source TV engine, Cobalt (built by
[TizenTubeCobalt](https://github.com/reisxd/TizenTubeCobalt)), and it loads this one file into
youtube.com/tv:

```
https://cdn.jsdelivr.net/gh/Vagii-Kavagi/VAG11TV-script@<version>/v.js
```

Each build of the app loads one exact tagged version (`SCRIPT_VERSION` in the app's
`cobalt/build_cobalt.py`), so the TV runs exactly the version that was tested. A change to `main`
alone reaches nobody.

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
3. Set `SCRIPT_VERSION` in the app's build tool to the new tag (five characters at most, such as
   `1.1.4`), rebuild and reinstall the app.
