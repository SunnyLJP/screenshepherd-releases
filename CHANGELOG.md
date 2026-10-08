# Changelog

Notable changes to ScreenShepherd. Format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versions follow
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

Only released builds appear here. Versions are cut from the private app repo
and published to this repo's Releases page.

## [0.2.9] — 2026-10-08

Sign in with Google, and fixes for the ways a long service could stop it
following or slow the computer down.

### Added

- **Continue with Google.** The sign-in screen has a "Continue with Google"
  button. It opens your browser at the ScreenShepherd website, you pick your
  Google account, and the app signs itself in. If you already signed up with
  Google on the website, your browser remembers you and the app links
  straight away.

### Fixed

- **One slow answer from ProPresenter no longer stops it following.** If
  ProPresenter took too long to reply even once, the app could stop noticing
  slide changes made in ProPresenter for the rest of the service while still
  showing green. It now carries on, and reconnects by itself if ProPresenter
  stops answering altogether.
- **It no longer signs a church out during a service.** The app now waits
  until a service is over to refresh its sign-in, and a dropped connection is
  treated as being offline, not as being signed out.
- **Less load over a long service.** It looks through the ProPresenter
  library less often while listening, saves its song cache without pausing,
  and no longer piles up work each time the audio input restarts.
- **The update is downloaded once.** An update waiting to install was being
  copied and checked again every six hours while the app stayed open.
- **Sending service logs no longer slows the app** on a computer that has
  been running for days.
- **The Control Panel stops drawing when it's hidden**, leaving more of the
  computer for ProPresenter.

## [0.2.8] — 2026-10-07

Steadier through a long service, one download for every Mac, and a Windows
build that hears properly.

### Fixed

- **It no longer falls behind when ProPresenter is busy.** With video or
  backgrounds playing on the same computer, the part of the app that picks
  singing out of the room was waiting its turn behind everything else, and
  the Control Panel said the computer was struggling. It now stays at full
  speed however busy the computer is.
- **A stray word can't change the song.** After a quiet moment, one word that
  also appears in another song could switch to it for a few seconds. A song
  change now needs several different words of the new song.
- **Restart listening really restarts.** From the menu, after allowing the
  microphone, or after signing out and back in, the app used to stay on
  "Starting…" until it was quit.
- **A Mac activated from the website stays activated.** On its second launch
  with internet, it could be sent back to the sign-in screen.
- **The vocal mics survive the desk being switched on late.** If the audio
  interface wasn't connected when the app opened, it could listen to input 1
  for the whole service instead of the channels you chose.
- **It picks up where it left off after a crash**, however far into the
  service, instead of coming back not listening.
- **A slow network at launch no longer asks a signed-in church to sign in.**
- **It always listens for English.** Every so often it tried to work out
  which language was being sung, and sometimes guessed wrong.

### Changed

- **One download for every Mac.** The same app runs natively on Apple
  silicon and on Intel Macs with macOS 14 or later, and works out which it is
  on by itself. Intel support is new: if anything doesn't behave, tell us.
- **Windows hears properly.** The Windows build now uses more of the
  computer's processor to listen, and ships the Microsoft components it needs,
  so it runs on a PC that has never had them installed. Still new: tell us
  how it goes.
- **An unplugged interface is named.** If the audio interface drops off its
  cable, the status says so by name and that it is waiting for it, and the
  app picks it back up by itself the moment it is plugged in again.
- **One voice model, and a smaller download.** The app uses its faster voice
  model everywhere, with no setting to change, and the download is about
  490 MB smaller.
- **It keeps the computer awake while it listens**, so a booth computer
  nobody touches during a service doesn't go to sleep mid-song.
- **Recordings no longer fill the disk.** The app keeps two weeks of its
  service recordings, up to 5 GB, and removes older ones.
- **Sign-in works behind a church network filter or proxy.**
- **Less work in the background.** Audio is converted more efficiently, and
  the app's windows stop drawing when nobody can see them, leaving more of the
  computer for ProPresenter.

## [0.2.6] — 2026-09-27

Speed, and two ways the screen could stop following.

### Changed

- **The slides land noticeably sooner.** The app now times itself when it
  starts and runs as fast as the computer it is on allows, instead of at a
  fixed pace set on one developer's Mac. On an M2 that is roughly twice the
  old rate. A slower computer gets a slower pace rather than falling behind,
  and the Control Panel still says so if it cannot keep up.

### Fixed

- **The screen no longer stops at the end of a chorus.** On a section that
  ended with a short line — a three-word tag like "Your Presence Lord" — the
  app was waiting for a kind of evidence that a line that short can never
  produce, and the screen stayed there for the rest of the song. It now waits
  to hear the next thing sung and goes wherever those words belong: on with
  the song, or round again if the band repeats.
- **It stops hopping between songs.** Running faster made the song detector
  accept evidence at the speed it arrived rather than the speed it was sung,
  and in one test it changed song six times in three minutes. It now needs
  real singing between one piece of evidence and the next.
- **A repeat written into the file goes forwards.** Where a church has typed
  the chorus in twice — Chorus, Chorus, Bridge — the second pass now moves on
  to the second copy instead of jumping back to the first, so the song still
  reaches the bridge.
- **It cannot go quietly deaf.** One failed piece of audio processing could
  stop the app listening for the rest of the service with nothing on screen
  to say so. It recovers now, and a run of unusable audio is cut short
  instead of holding everything up.
- **Less lost at the start of a line.** Words are no longer discarded by a
  measurement that was reading about a third less singing than was there.

Mac: requires macOS 14 or later, Apple silicon. Windows: 10 or 11, 64-bit,
not yet code-signed — SmartScreen asks once before the first run.

## [0.2.5] — 2026-09-23

0.2.4 was built and withdrawn before it was published: its first quit wrote
inside its own app bundle, and macOS then refused to open it. 0.2.5 is the
same release with that fixed.

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
