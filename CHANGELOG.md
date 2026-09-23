# Changelog

Notable changes to ScreenShepherd. Format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versions follow
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

Only released builds appear here. Versions are cut from the private app repo
and published to this repo's Releases page.

## [0.2.4] — 2026-09-23

### Added

- **Announcements.** When the presentation on screen is a deck of notices
  rather than a song, the app follows the host: as they talk about an item,
  the matching slide comes up. It listens for each slide's name and text, and
  reads the words off the slide's picture too.
- **It listens with nothing on screen.** With ProPresenter on the logo, or
  cleared to black, the first song the band starts is found and opened on
  the line being sung. No more opening the first song by hand.
- **ProPresenter on another computer.** The address field is back in setup
  and settings, pre-filled for the usual case of ProPresenter on this
  computer.
- **Windows: every desk channel.** The input picker lists ASIO drivers
  beside Windows' own devices, so a USB desk offers all of its channels, not
  the stereo pair Windows sees.

### Fixed

- **A silent input says so.** If the audio interface stops delivering sound,
  the Control Panel goes to Needs attention within a few seconds and names
  the device, instead of staying green. Reconnecting recovers on its own.
- **Fewer words lost.** A filter that had been discarding real singing on
  busy stages is off. In one test it had thrown away one in seven sung
  windows.
- **Words back sooner** after a long instrumental: a confidently matched
  line puts the slide back.
- **One computer type.** The developer console and the services page are
  gone; every account sees the same app.
- The account page names each computer by its actual name instead of
  calling all of them "This computer".

Mac: requires macOS 14 or later, Apple silicon. Windows: 10 or 11, 64-bit,
not yet code-signed — SmartScreen asks once before the first run.

## [0.2.3] — 2026-09-20

### Fixed

- **Windows finds your audio devices.** The first Windows build asked the
  ASIO drivers for devices and got one entry per driver, slowly, or nothing.
  It now lists what Windows' own sound settings list.

## [0.2.2] — 2026-09-20

### Added

- **Windows.** A 64-bit installer, from the same release as the Mac build.
  Not yet code-signed: SmartScreen asks once before the first run.

### Fixed

- Setup asks for the microphone, and a remembered input now opens without
  being re-chosen. (Mac, 2026-09-19.)

## [0.2.1] — 2026-09-19

### Added

- A first-run walkthrough for a church that has just paid.

## [0.2.0] — 2026-09-19

### Added

- **Sign in to activate.** The app asks for an email and password the first
  time it opens. There is no licence key to paste.
- **A 7-day free trial, then a subscription.** A card is taken at signup and
  nothing is charged until the trial ends.
- **Create an account from the Mac.** Pressing **Create an account** on the
  sign-in card opens the browser, and the Mac links itself when signup
  finishes.
- **Email confirmation.** Signing up sends one email; tapping it finishes the
  setup. If the Mac's sign-in card says the address is not confirmed yet, it
  offers to send the link again.
- **Manage account** in settings opens your account page already signed in —
  billing, your card, and your password live there, because the app runs
  with the wifi off.
- **Email**, for the things that matter: a welcome, a warning before the trial
  ends, and a note when a computer is activated.

### Changed

- One radius everywhere. Nothing in the app is a pill any more.
- The wordmark reads ScreenShepherd, one word, like everything else.
- The developer console is no longer offered to every church. It is ours.

### Removed

- Keyboard shortcuts.

## [0.1.2] — 2026-09-14

*Built and tested, never uploaded. The fixes below shipped in 0.2.0.*

Two fixes found in real services on 13 September.

### Fixed

- **Section jumps.** Going back to a chorus, or to any earlier section, could
  be recognised and then refused, every time, for a whole service — while
  ordinary forward advances kept working. On some ProPresenter versions a
  check the app made before every jump could never pass. It fires now.
- **Changing songs.** If ProPresenter was briefly unreadable at the moment of
  a song change — which is exactly when it is busiest — the app could keep
  showing the previous song's slides until the next song change. It retries a
  second later now.


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
