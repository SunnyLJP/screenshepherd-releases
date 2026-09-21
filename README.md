# ScreenShepherd releases

Downloads and release notes for **ScreenShepherd** — an on-device listening
engine that follows a live singer and drives ProPresenter 7 through a service.

This repo is public so that the app can check for updates without shipping a
GitHub token, which is the only reason it exists. **It holds no source code.**
The app, the site and the docs live in their own repos, and those are private.

## Downloads

Every build is published to [Releases](https://github.com/SunnyLJP/screenshepherd-releases/releases).

- **Mac:** the `.dmg` is what you want. The `.zip` is what the auto-updater
  uses — you can ignore it.
- **Windows:** the `-x64-setup.exe`, from 0.2.2 on.

The Mac build is signed with a Developer ID and notarised by Apple, so macOS
opens it normally — no warnings and no right-clicking.

The Windows build is not yet code-signed, so SmartScreen shows **Windows
protected your PC** on first run. Press **More info**, then **Run anyway**.
The file is exactly what this page lists: check the SHA-512 in `latest.yml`
if you want to be sure.

**ScreenShepherd needs a subscription.** The download is open to anyone, and
the app asks you to sign in the first time it opens. Start a free trial at
[screenshepherd.live](https://screenshepherd.live).

## Requirements

- **macOS 14 (Sonoma) or later**, Apple silicon. Not macOS 13 — the audio
  engine uses a Metal API that does not exist there, so it cannot launch.
- or **Windows 10 or 11**, 64-bit. Transcription runs on the CPU on Windows,
  so a machine from the last few years is a good idea.
- ProPresenter 7, with **Settings → Network** enabled.
- An audio interface, and a channel carrying the vocal.

## Release notes

See [CHANGELOG.md](CHANGELOG.md), and the notes on each individual release.

## Documentation

Setup, the live-service runbook and the safety model are documented at the
docs site. Issues on this repo are for **downloads and updates only** — it is
a distribution point, not where the app is developed.

## For the maintainer

Nothing that signs, notarises or publishes a build is in this repo, and no
GitHub token ships in the app. The credentials and the release procedure are
documented in the private app repo (`SECRETS.md` and `CLAUDE.md`).
