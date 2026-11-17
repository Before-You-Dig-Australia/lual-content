# Look Up and Live: test content

A Content Bundle for testing content updates in Look Up and Live before the Filament app exists.

The store builds fetch from `https://content.lookupandlive.com.au/v1/bundle.json` (ADR 0006 in `lual-capacitor`), which isn't hooked up yet. To test against this repo, build the app locally with `VITE_REMOTE_BUNDLE_URL=https://raw.githubusercontent.com/Before-You-Dig-Australia/lual-content/main/v1/bundle.json` in `lual-capacitor`'s `.env.local`, and take it out before any upload. The app fetches the bundle each time it opens or comes back to the foreground.

## To change the content

1. Edit `v1/bundle.json` (on GitHub, the pencil icon).
2. Set `publishedAt` to the current date and time, in UTC, such as `2026-11-18T03:00:00Z`. A bundle older than the content in the app is ignored.
3. Commit to `main`.
4. On the phone, switch to another app and back (or close and reopen it), then open the Page from the menu.

GitHub caches the file for up to about 5 minutes. If the file isn't valid (a missing comma, a field the app doesn't expect), the app keeps its current content and reports the problem to Sentry.

To start again from the content in the app, run `npm run content:bundle -- <path to this repo>/v1/bundle.json` in `lual-capacitor`.
