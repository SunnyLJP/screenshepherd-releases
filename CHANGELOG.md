# Changelog

Notable changes to ScreenShepherd. Format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versions follow
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

Only released builds appear here. Versions are cut from the private app repo
and published to this repo's Releases page.

## [Unreleased]

## [0.1.1] — 2026-09-12

Built for a service running on a mac that has never seen it, with ProPresenter
possibly on another machine and a leader still changing their mind.

### The voice ships inside the app

No download on first launch. Install it and it is ready, even with no internet
at all. The download is larger for it; the day is not.

### Fixed — songs added or reordered mid-service

- **A song added to the playlist during a service is now picked up.** It used
  to be invisible until something else changed the presentation, which meant a
  band could play a whole song while the app sat holding — with no way out
  short of restarting it.
- **Reordering a song's sections while it is on screen no longer fires the
  wrong slides.** Only a change in the number of slides was noticed before.
- **The setup tab shows tonight's songs**, how many are ready, and a
  **refresh** if you would rather not wait the few seconds.

### Fixed — ProPresenter on another machine

- It says which machine and which address it cannot reach, and tells apart
  "never connected" from "lost it".
- Pasting an address with `http://` on the front now works.
- Names the macOS local-network permission, which otherwise fails silently
  forever once declined.
- The engine no longer stops when that machine drops off the network — and if
  it ever does restart mid-service, it comes back listening.

### Fixed — audio

- A microphone renamed by macOS no longer leaves the app showing a device that
  is selected while hearing nothing. It says which input is missing.
- Says when macOS is blocking the microphone, and recovers once it is allowed.

### Changed

- Updates install themselves, quietly, ready the next time the app opens —
  and never while it is listening.

## [0.1.0] — 2026-09-10

The first release that can be downloaded. Signed with a Developer ID
certificate and notarised by Apple, so macOS opens it normally.

### What it does

- Follows the lead singer and advances ProPresenter through a service —
  slides, sections and song changes.
- Runs entirely on the Mac in the booth. Nothing leaves that machine during a
  service, and it works with the wifi off.
- Puts a bible passage on screen when one is read out in the talk, and takes
  it away afterwards.
- Guided setup on first run, and a microphone check that reads back what it
  heard so you can confirm the right channel.
- Global shortcut keys, so the operator can stay in ProPresenter.

### Requires

- macOS 14 (Sonoma) or later, Apple silicon. It will not run on macOS 13.
- ProPresenter 7 with **Settings → Network** switched on.
- An audio interface with the lead vocal on its own channel.
