# ScreenShepherd releases

Downloads and release notes for **ScreenShepherd** — an on-device listening
engine that follows a live singer and drives ProPresenter 7 through a service.

This repo is public so that the app can check for updates without shipping a
GitHub token, which is the only reason it exists. **It holds no source code.**
The app, the site and the docs live in their own repos, and those are private.

## Downloads

Every build is published to [Releases](https://github.com/SunnyLJP/screenshepherd-releases/releases) as a `.dmg` (what you
want) and a `.zip` (what the auto-updater uses — you can ignore it).

Every build is signed with a Developer ID and notarised by Apple, so macOS
opens it normally — no warnings and no right-clicking.

**ScreenShepherd needs a subscription.** The download is open to anyone, and
the app asks you to sign in the first time it opens. Start a free trial at
[screenshepherd.live](https://screenshepherd.live).

## Requirements

- **macOS 14 (Sonoma) or later**, Apple silicon. Not macOS 13 — the audio
  engine uses a Metal API that does not exist there, so it cannot launch.
- ProPresenter 7, with **Settings → Network** enabled.
- An audio interface, and a channel carrying the vocal.

## Release notes

See [CHANGELOG.md](CHANGELOG.md), and the notes on each individual release.

## Documentation

Setup, the live-service runbook and the safety model are documented at the
docs site. Issues on this repo are for **downloads and updates only** — it is
a distribution point, not where the app is developed.
