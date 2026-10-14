## v0.6.47 — 2026-10-14 — The changelog fills in its gaps

- **No change to either product.** Eleven earlier releases, v0.6.16 to
  v0.6.26, now have their notes: the macOS 10.15 minimum and disk-image
  installers, the full fine-tune range, hex parameters shown in hex, Top Key
  kept to the keyboard, sample-accurate MIDI in Mample, and a fix for notes
  that could keep sounding after a key was struck twice. A release can no
  longer be made without its notes.

## v0.6.46 — 2026-10-13 — A flaky internal test made repeatable

- **No change to either product.** The internal test that compares DSKlusion
  and Mample now gives both the same simulated filter components, so it no
  longer fails about one run in twenty. Each plug-in instance still gets its
  own analogue component spread, exactly as before.

## v0.6.45 — 2026-10-13 — Plug-in validation passes; sample loading starts from the Mirage's own settings

- **Pitch Bend's displayed value now reads back exactly.** Hosts that type
  or store the parameter as text no longer see the last digit drift. It now
  shows 4 decimals; its range, default and automation are unchanged.
- Both products now pass clap-validator, the CLAP format's standard checker,
  as well as pluginval at its strictest level.

- **The sample-load dialog's Load button works on a fresh instance.** The
  sampling parameters P73-P77 (sample time, input filter, line level,
  threshold, multisampling) now start at the Mirage boot disk's values -- P73
  34, P74 80, P76 24 -- and the dialog sees them, instead of zeros that kept
  Load disabled. In LLE the dialog shows the running OS's own values.

## v0.6.44 — 2026-10-13 — Tests can no longer touch your own settings

- **No change to either product.** Every internal test now runs in test mode,
  where settings and logs go to a temporary folder. 30 tests could previously
  run without it and so reach the user's own `Documents\KnivesOnStrings`
  folder. The test run now checks this first and stops if any test would
  run outside test mode.

## v0.6.43 — 2026-10-13 — Damaged disk images say so; window scaling in Live is tested

- **A damaged disk image now says so when it loads.** An `.hfe` with missing
  or unreadable sectors -- typically a partial conversion -- still loads, since
  its intact sounds may play, but the status line names the image and what is
  affected, for example *15 of 480 sectors missing and 1 unreadable (OS,
  Lower 1 parameters, Lower 1 samples)*.
- **A disk whose system parameters are out of range is no longer trusted.** If
  a disk's OS 3.2 system block holds a global the Mirage's own panel cannot
  set (for example a master tune above 99), HLEv2 ignores the block and keeps
  its defaults, instead of detuning every voice. The log says which value it
  refused.

- **A damaged disk mounts write-protected**, so the Mirage cannot save to a
  disk with missing or unreadable sectors. Reopening the editor shows the
  warning again.
- **WINDOW SCALE resizes correctly in hosts that scale plug-in windows**, such
  as Ableton Live with Auto-Scale Plug-In Window on: the window's size limits
  are now set in the host window's DPI context. Both products' resizing is now
  checked in a test host on every build.

## v0.6.42 — 2026-10-12 — HLEv2 plays out-of-range notes as the Mirage does; velocity parameters keep their whole byte

These affect the HLEv2 engine in both Mample and DSKlusion.

- **MIDI notes outside the Mirage's keyboard (36–96) now play the key the
  Mirage folds them to**, by octave: the folded key's pitch, wavesample and
  half. Two notes an octave apart both sound. Retrigger and the sustain pedal
  work per incoming note, and pedal-up releases only that note's own voice.
- **Velocity parameters P45/P46/P48/P49 and P55/P56/P58/P59 keep their whole
  stored byte**, as OS 3.2 does, so edits, undo, copy and save no longer lose
  the low bits. The amp release's velocity shift (P59) now comes off the
  rate-table step, as on the Mirage. The panel still shows the byte divided by
  4, capped at 31.

## v0.6.41 — 2026-10-12 — Up to 32 tags per sound half

- **A sound half can now carry up to 32 tags** (it was 16). Each tag is still
  up to 64 characters. ADD CATALOG TAGS counts only the tags that fit.

## v0.6.40 — 2026-10-12 — Tag your sounds, and share your labels

- **Tag your sounds.** In the disk library's editor, each half of a sound --
  Lower and Upper -- can carry tags: your own words, up to 16 per half, 64
  characters each, with suggestions that start from keys, strings, brass &
  wind, synth, percussion and voice. Tags match without regard to A-Z case;
  accented letters are different tags ("É" and "é"). **Apply to both
  halves** copies one half's tags to the other. A comma separates tags, typed
  or pasted, and the editor says when a tag is longer than will be kept.
- **Your labels file.** Tags and program names live in your own labels file,
  `disk_catalog.user.json`, beside the catalogue; SAVE never writes them into
  `disk_catalog.json`. A disk or sound name you change with SAVE goes into
  both files, and the labels file wins.
- **Find sounds by tag.** The library's search matches tags as well as names,
  and clicking a tag on a sound shows only the disks that carry it. The tag
  you are filtering by shows as a chip you click to clear.
- **EXPORT MY LABELS…** in the disk library saves your labels to a file you
  can send us, so they can go into the catalogue everyone gets: your labels
  file, plus the disk, sound and program names you saved before this version.
  It holds only the disks' content IDs and your labels: no file names, folders
  or user names. Tags you added before this version were never saved, so
  there are none to export.
- **Both products show the same labels.** A name or tag you give a disk in one
  product shows in the other the next time its disk library is opened.
- **A disk without a content ID can't be given tags or program names**; the
  editor says so, and its names can still be changed.
- **When your labels can't be saved, the library says so** and puts back
  whatever was not kept, rather than showing an edit that was lost. After a
  SAVE in the editor it says which part was kept: the names, or nothing.
- **Merged labels reach existing installs.** When a release ships a newer
  catalogue, the tags of every half you haven't tagged yourself follow it,
  and every name you haven't changed -- a disk's title, a sound's name, a
  sound's program names -- takes its name. A name you changed keeps yours,
  name by name: renaming one sound no longer stops the rest of the disk
  following the catalogue. A disk saved by an earlier version keeps all its
  names.
- **Your own labels always win over catalogue updates.** A newer catalogue
  never replaces a name you changed or the tags you gave a half; only USE, or
  ADD CATALOG TAGS, brings the catalogue's back.
- **"Catalog: <name>", with USE.** Where a title, sound name or program name
  in the editor differs from the catalogue's own, a line under it shows the
  catalogue's name; **USE** puts it back at once, in your labels file and the
  catalogue, and from then on that name follows the catalogue again.
- **ADD CATALOG TAGS.** A sound half with tags of your own is offered the
  catalogue's tags it lacks: **ADD CATALOG TAGS (n)** adds them all after
  yours, a faint **+tag** chip adds one. Nothing is removed; 16 at most.
- The shipped catalogue is now version 2.4.

- **A tagged sound appears under the sound-type chip its tags name**, whatever
  its name says, and a half tagged only with words that name no chip (just
  "pad", say) appears under no chip. A sound without tags is still sorted by
  the words in its name.
- **Program names you edit in DETAILS are now kept in your labels file**, like
  tags.

## v0.6.39 — 2026-10-11 — DSKlusion shows the Mirage OS MIDI setting; MASOS's keyboard plays on its own channel

- **Settings → MIDI now shows what the Mirage OS itself listens on** (P81 omni,
  P82 channel), read-only, and warns in LLE when the OS would ignore notes the
  plug-in passes to it.
- **Under MASOS the on-screen keyboard now plays on MASOS's own MIDI channel.**
  It used to send on channel 1, which MASOS ignored when omni was off.
- The plug-in's MIDI receive channel is system-level state, and a disk's P81/P82
  never drives it (owner decision, 2026-10-11). The Settings line reports the
  OS's setting; it does not change what the plug-in accepts.

## v0.6.38 — 2026-10-11 — HLEv2 reads a disk's MIDI channel settings from the right place

- **Internal: HLEv2 reads a disk's MIDI omni and channel settings from where
  OS 3.2 keeps them.** There is no change to how either product responds to
  MIDI: each still filters on its own receive channel.

## v0.6.37 — 2026-10-11 — Mix-mode sounds play the Mirage's wavesample pairs; Keyboard Balance works

These affect the HLEv2 engine in both Mample and DSKlusion.

- **With mix mode on (P28), each key plays the wavesample pair the Mirage
  plays**: two at a time, with the second layer the next wavesample up. This
  fixes several piano and MELPRO sounds that played the wrong wavesample on
  some keys.
- **Keyboard Balance (P24) now balances the two halves as the Mirage does.**
  Every library disk ships it centred, so loading a sound sounds the same;
  editing it is now audible.
- **Relative Amplitude (P69) sets levels exactly as the Mirage decodes it.**
- **The second layer of a mix-mode sound plays at the first layer's P69
  level**, as on the Mirage. This changes the level of about 20 library
  sounds; for example, the second layer of #7 clarinets was silent and now
  sounds.

## v0.6.36 — 2026-10-11 — Master tune and bend range are one setting for the whole instrument

These affect the HLEv2 engine in both Mample and DSKlusion, except the last
item, which affects both editors.

- **Master tune, bend range, velocity curve, keyboard balance and link
  (P21–P25) and P78–P80 are one setting for the whole instrument**, as on the
  Mirage. A master-tune edit retunes both halves, and notes already held.
- **The pitch wheel's range follows P22**, as measured on the Mirage.
- **MIDI controllers 2–7 and channel pressure now reach the engine** where the
  sound assigns them (P78/P79).
- **Window resizes run in the host window's DPI context**, so the editor
  sizes correctly under Ableton Live's plug-in auto-scale.

- **In LLE the pitch wheel rests exactly on centre.**

## v0.6.35 — 2026-10-11 — Decay follows the key; two-layer sounds mix as on the Mirage

These affect the HLEv2 engine in both Mample and DSKlusion.

- **Decay now scales by key (P47/P57)**, as on the Mirage: on sounds that use
  it (about 20% of the library), higher notes decay faster.
- **Two-layer programs mix as measured on OS 3.2.** At P35 = 0 the mod wheel
  crossfades the two layers live, while the note sounds; at P35 above 1,
  velocity feeds the mix.
- **The second layer keeps sounding at the DOC volume floor** (about −27 dB)
  where it used to go silent, as on the Mirage.

- **Undo, redo, copy and keypad edits keep P47/P57's exact stored byte.**

## v0.6.34 — 2026-10-10 — Each half vibratos with its own LFO

These affect the HLEv2 engine in both Mample and DSKlusion.

- **Each half's sound now vibratos with its own LFO speed and depth (P31/P32)**,
  as the Mirage does. This matters when the Lower and Upper halves come from
  different sounds or disks: each keeps its own vibrato instead of both
  following the Lower half's.
- **The LFO no longer moves the filter.** It never did on the Mirage. Sounds
  with vibrato may sound slightly different.
- **Layer B keeps its vibrato and pitch bend through the release.**
- **LFO edits take effect on the next note**, as on the Mirage.

## v0.6.33 — 2026-10-10 — SAVE DISK never writes the wrong disk

- **SAVE DISK never writes the wrong disk.** It saves the disk that was in
  the drive when you started, into the file you chose for it. Changing disks
  while the save dialog is open no longer puts one disk's contents into the
  file chosen for another.
- **The disk-write confirmation describes the disk actually in the drive**,
  with its real write-protect state, and says "(empty drive)" when there is
  none. A write you confirm goes only to the disk you confirmed it for.
- **A write-protect toggle is never lost.** Toggling the disk in the drive and
  then a disk waiting to go in no longer drops the first toggle (which could
  let the firmware write a disk you had protected).
- **A refused write-protect toggle says so.** If the drive can't take the
  change, you get an error instead of a record claiming a state the drive
  doesn't have.
- **P27 (initial wavesample) and P28 (mix mode) are now kept per program**, as
  the Mirage keeps them. No control edits them for a named program yet, so
  nothing changes in use; when one does, the edit reaches that program
  instead of the one playing.

## v0.6.32 — 2026-10-10 — Four tests now check in Release builds

- **No change to either product.** Four internal tests now run their checks
  in Release builds as well as Debug, and a dead internal test-tone helper
  was removed.

## v0.6.31 — 2026-10-10 — Mample's VOLUME knob works on older macOS

- The shared web bundle's JUCE script is now built for older WebKit too, so
  DSKlusion's controls load on the same older macOS versions.

---

## v0.6.30 — 2026-10-10 — LLE sample loads and edits reach the running OS safely

- **In LLE, loading a sample into the Mirage's memory no longer races the
  running OS.** The sample is now handed to the audio engine and copied in
  at the start of its next block, so the OS never plays, and the waveform
  never shows, a page that is half old sample and half new.
- **If a sample load is still waiting for audio, it says so.** In LLE, a
  second LOAD SAMPLE made before the first has reached a running audio
  engine now shows "Sample load pending -- start audio and try again"
  instead of "Error", and the button stays ready for the retry.
- **The LLE waveform display no longer reads memory the OS is writing.**
  It now shows a copy the audio engine takes between blocks, so the picture
  cannot be torn mid-load. It can lag the sound by about a second.
- **In LLE, editing a named wavesample or program changes the sound.** An
  edit addressed to a particular wavesample or program, rather than the one
  currently selected, used to change only the display copy and never reach
  the running OS. It now reaches the OS for that slot, and shows once that
  wavesample or program is selected.
- **SAVE DISK with no disk in the drive saves nothing.** After an eject,
  saving the disk could write out the ejected disk's contents. It is now
  refused, including when the eject and the save happen at the same moment.

- Two internal tests were made reliable: one no longer depends on thread
  timing, and one now checks its parameter layout in release builds too.
  Neither product's behaviour changes.

## v0.6.29 — 2026-10-10 — The macOS floor is stated per Mac

- **Both products state the macOS they need for each kind of Mac:** macOS
  10.15 Catalina or later on an Intel Mac, macOS 11 Big Sur or later on an
  Apple Silicon Mac. The installer welcome text, the disk-image README and
  the Mample manual now say so; before, they gave 10.15 for both.
- **The macOS packager checks it.** Every packaged build is verified to
  start on exactly those versions, for each architecture.

## v0.6.28 — 2026-10-10 — A held mod wheel survives a LOAD

- **In HLEv2, a held mod wheel keeps its effect after a LOAD or a sample
  load.** Before, the new sound started with the wheel at zero and the
  wheel did nothing until you moved it again.

## v0.6.27 — 2026-10-09 — In HLEv2, what you edit is what you hear

- **Edits in HLEv2 change the sound.** A parameter changed in HLEv2 -- in
  the parameter drawer, on the waveform, by undo, redo or a copy between
  halves, or with the Mirage's own PARAM and VALUE keys -- now changes the
  sound HLEv2 plays, from the next note, and shows at once. Before, these
  edits changed a copy HLEv2 did not play, and the drawer could go back to
  the old value.
- **The drawer marks edited parameters in HLEv2**, as it does in LLE: a value
  that differs from what the disk loaded is shown in bold.
- **A sample loaded in HLEv2 is the sample you hear**, and the waveform shows
  it. In HLEv2 the waveform now always shows the sound HLEv2 plays; before,
  it showed what LLE's machine last held.
- **LOAD in HLEv2 keeps the other half's edits.** Loading a sound into one
  half leaves the other half as you edited it.
- **HLEv2 no longer writes into LLE's sample memory.** It used to write the
  parameters' values into one page of it on every audio block, which LLE then
  played as part of any sample stored there.
- **In LLE, an edit no longer disturbs the running Mirage.** Changing a
  parameter from the drawer or the panel used to move the running OS's
  sample-memory bank and write a byte into the sample memory being played,
  which could click or cut a loop. It now changes the parameter only.
- **The audio thread no longer allocates memory on every block**, in either
  engine, which could cause dropouts in some hosts.
- **Not yet:** in HLEv2, DAW automation of the Mirage's parameters is not
  heard. Edits are not stored in your DAW project: a reopened project starts
  from the disk, as before.

## v0.6.26 — 2026-10-09 — macOS notarizing is more reliable

- **No change to either product.** The macOS notarizing script now clears a
  leftover disk image and gives up on a stalled upload instead of hanging.

## v0.6.25 — 2026-10-09 — Notes land on time; a re-struck key releases cleanly

- **Fixed: in HLEv2, striking a key again before releasing it could leave a
  note sounding.** Overlapping notes on the same key, a doubled controller,
  or re-striking a key the sustain pedal holds could leave one voice held
  until another note took it over. Every note now releases.

## v0.6.24 — 2026-10-09 — Top Key keeps to the keyboard

- **P72 Top Key now ranges 1-61, the Mirage's own panel range.** It used to
  accept 0-127, values no Mirage disk can hold; the default is now 61.

## v0.6.23 — 2026-10-09 — The Mirage panel shows hex parameters in hex

- **In HLEv2, the panel shows hexadecimal parameters as the Mirage does.**
  P60-P64, P66, P68, P97 and P99 display as two hex digits, as OS 3.2's own
  display shows them, and typing a value for one takes hex digits.

## v0.6.22 — 2026-10-08 — Fine tune uses its full range

- **P68 Fine Tune now uses the Mirage's own 0-255 range**, shown in hex as
  on the Mirage, from disk to sound to save. It was a 0-99 value converted
  on load, which lost detail and could write the wrong byte back. Factory
  sounds play at the same pitch as before.

## v0.6.21 — 2026-10-08 — Internal tooling

- **No change to either product.** Shared project tooling was brought up to
  date.

## v0.6.19 — 2026-10-08 — The Mac installer comes on a disk image

- **On macOS, each product now ships as a signed, notarized disk image.** It
  holds the installer package, a read-me, the licence texts and an
  uninstaller, and Mample's also holds its manual.
- The licence agreement no longer opens with an internal draft note.

## v0.6.18 — 2026-10-07 — Contact addresses

- **The licence agreement and the Mample manual give our
  knivesonstrings.com addresses**: legal@, privacy@, support@ and hello@.
  Bug reports still go to the GitHub issues.

## v0.6.17 — 2026-10-07 — Both products run on macOS 10.15 Catalina

- **The macOS minimum is now 10.15 Catalina** on Intel Macs (Apple Silicon
  Macs start at macOS 11). It was macOS 11 Big Sur. Keep Safari up to date on
  10.15: the interface uses its web engine.

## v0.6.16 — 2026-10-07 — Internal tooling

- **No change to how either product works.** Shared project tooling was
  brought up to date, and the Mample manual gives hello@knivesonstrings.com
  for general questions.

## v0.6.15 — 2026-10-06 — HLEv2 shares LLE's floppy drive

- **HLEv2 and LLE now use one floppy drive.** The disk you mount is the disk
  both engines see. In HLEv2, mounting a disk puts it in the drive and loads
  nothing: the sound you are playing keeps playing, as it does on the Mirage
  and in LLE. Before, mounting in HLEv2 replaced the sound in both halves.
  When HLEv2 has nothing loaded yet (a new instance, or RESET with no disk),
  mounting a disk also loads its sound 1 into both halves, as a Mirage
  waiting for a disk boots the one you put in.
- **LOAD in HLEv2 loads one half, from the disk in the drive.** LOAD LOWER or
  LOAD UPPER, a digit and ENTER put that sound into that half only; the other
  half keeps the sound it has. Before, a LOAD reloaded both halves from the
  disk file.
- **With no disk in the drive, LOAD shows "nd"** in HLEv2, as the Mirage does,
  and loads nothing.
- **Switching engines keeps the disk.** Switching from LLE to HLEv2 loads from
  the disk in the drive, including anything the Mirage has written to it that
  is not in the disk's file yet, and switching back finds the same disk. RESET
  in HLEv2 starts from the disk in the drive too; with the drive empty, it
  starts with nothing loaded.
- **Switching from LLE to HLEv2 with no disk in the drive starts HLEv2 with
  nothing loaded.** Before, it loaded the last disk's file. Mount a disk to
  hear it.
- **The disk browser's hint is the same in both engines** ("insert to make it
  available to the panel"). It used to say HLEv2 had no drive.

## v0.6.14 — 2026-10-05 — A Windows installer for Mample, and no ASIO

- **ASIO is no longer supported.** On Windows the standalone apps play through
  Windows Audio (WASAPI) or DirectSound. Plugins in a DAW are unaffected: there,
  audio devices belong to the host. The ASIO notices are gone from the About
  box and the licence texts with it.
- **The About box says "Beta Tester Version"** under the version.

- **Fixed: opening or mounting a disk just as another load finished could be
  mistaken for a restart.** For an instant DSKlusion could read the new load as
  a cold boot: it might show the Booting Firmware overlay, refresh the waveform
  before the new sound had loaded, or report a mounted disk before it was in
  the drive.

## v0.6.13 — 2026-10-04 — Mample's network code is the shared client

- Nothing changes: DSKlusion still makes no network connections, and every
  build now checks that its plugin files contain neither of Knives on
  Strings' server addresses.

## v0.6.12 — 2026-10-03 — A disk mounted mid-load says what happened

- **Fixed: mounting a disk while a sound was still loading reported a failure,
  then put the disk in anyway.** In LLE, mounting a disk from the browser
  while an Open Disk or a reopened session was still loading cancelled the
  earlier load, and that cancellation was read as the new mount failing. The
  mount now reports what actually happened to it: in the drive if it went in,
  and a failure — saying why — only if it did not.

## v0.6.11 — 2026-10-03 — Open Disk loads both halves

- **Fixed: Open Disk in LLE loaded only the lower half of a sound.** With the
  Mirage's own OS 3.2 running, opening a disk — or reopening a session —
  loaded the lower half, then pressed LOAD UPPER while the drive was still
  reading it. The Mirage doesn't read its keys during a disk transfer, so the
  upper half kept whatever sound it had before. DSKlusion now waits until the
  drive has finished before pressing the next key, so both halves load, and
  the load finishes sooner than it used to.
- **The waveform view shows the sound you just opened.** It used to redraw
  before an Open Disk had finished, so for a second or two it could show the
  upper half's old waveform.

- **A save on the Mirage's panel now reaches the disk file on your computer
  (LLE).** When the Mirage's own OS finishes saving — a sound, a sequence or
  its configuration — DSKlusion writes the disk in the drive back to the file
  it came from, a moment after the drive goes quiet, even with the plugin
  window closed. There is no second prompt: the save already asked at ENTER.
  The file is backed up first, into that disk's own backups; if the backup
  can't be made, the file is left as it was.
- **A disk that can't be written back asks where to keep a copy.** An `.hfe`
  or `.edm` image, a raw image without the `.img` extension, or a file or
  folder you can't write to opens the Save dialog, filled in with your User
  Library (with a number added if the name is taken). The copy then takes the
  original's place — in the drive, if that disk is still in it — so later
  saves go to the copy, and the original is never changed. If the window was
  closed when you saved, the dialog opens when you next open it. If you
  cancel, or the write fails, the change stays on the disk in the drive while
  that disk is still there.
- **A save reaches its file even across a disk change.** Saves you make while
  the dialog is open, or just before you mount another disk from the browser
  or eject this one, each reach their own disk's file, or their own copy for a
  disk that can't be written back. When a change ends up on no file — its
  dialog cancelled, or its write failed, once its disk had left the drive —
  the message in the window says so, if it is open. A save that is not
  written, for any reason, is recorded in DSKlusion's log when logging is on
  (Settings → Logging; it is off by default).
- **Restoring a backup of the disk in the drive now asks you to eject it
  first.** The drive keeps the disk as it was put in, so that disk's next
  save would have written the old version straight back over the restore.
  Eject it, then restore.
- **SAVE DISK • now means "not yet in a file".** The dot goes out once a save
  reaches the disk's own file — a SAVE DISK back over it included — and stays
  lit when a write failed or the dialog was cancelled. It lights and goes out
  on its own now, instead of waiting for something else on the screen to
  change. SAVE DISK stays, for saving under another name or in another
  place; for a disk that can't be written back, the copy it saves takes the
  disk's place in the drive, wherever you save it.
- **Fixed: a save could overwrite a disk with its previous version kept
  nowhere.** A disk's backups are numbered through the day. Once the cleanup
  that keeps only the number you ask for had removed one from the middle of
  the day's list, the next backup took the number it freed, counted as the
  oldest, and was deleted by the cleanup that runs straight after every
  backup — before the file was overwritten. With the default of 10 kept, this
  began on the thirteenth save of one disk in a day, and SAVE DISK could reach
  it. Each backup is now numbered one past the day's highest, and a save is
  stopped, leaving the file as it was, if the backup it just took has gone
  (unless you keep only the original).
- In HLEv2, saving from the panel comes in a later update.

## v0.6.9 — 2026-09-30 — Every disk keeps its own backups

- **Each disk's backups are kept by where the disk lives.** Backups used to
  share one folder and were told apart only by filename, so two disks with
  the same name — a factory disk and your User Library copy of it, say —
  shared one list, and DSKlusion refused to restore either. The backup folder
  now holds a `library` and a `sounds` folder that mirror your User Library
  and Sound Disks folders, and each disk's backups go in the folder that
  matches its own. BACKUPS shows only that disk's backups, and a restore puts
  one back over that disk and no other.
- **The backups you already have move to match, and none is deleted.** The
  first time in a session that you open BACKUPS, save or restore, each
  existing backup that records which disk it was taken of moves into that
  disk's folder. Backups of disks kept anywhere else stay where they are.
  Backups that cannot be matched to a disk's current place stay in the
  backups folder itself: they no longer appear in a disk's BACKUPS list, and
  nothing is deleted.
- **Moving or renaming a disk inside your User Library takes its backups with
  it,** when DSKlusion recognises it as the same disk — unchanged since its
  last scan — the next time it scans the library or the disk is loaded.
- **A restore first keeps a backup of what it replaces,** so a restore can
  itself be undone from the same list.
- **A damaged backup record no longer costs you your backup history.** It is
  kept beside the new one, under a name ending in `.unreadable-` and the date.

## v0.6.7 — 2026-09-30 — The LLE engine starts the same way every time

- **The LLE engine starts the same way every time.** Six of the emulated
  6809 processor's registers started with whatever happened to be in memory,
  so two boots of the same disks could come out slightly different. They now
  start at zero. On the real chip these registers are undefined after
  power-up, so any fixed value is as faithful as any other; zero makes every
  boot repeatable.

## v0.6.6 — 2026-09-29 — A damaged catalogue is never saved over

- **A damaged disk catalogue is never saved over.** If the catalogue file
  that holds your disk names and protection tabs could not be read, the next
  library scan or details save used to replace it with a fresh one, and every
  name and tab in it was lost. Now nothing is written to it: the disks still
  list, and the file stays as it is so it can be recovered.
- **Merging two catalogue entries for the same disk keeps its protection.**
  When the same disk turned up under two names, the entries were merged and
  only one of them decided whether the disk stayed protected, so a protected
  factory disk could come out writable. Now the merged disk is protected if
  either entry was, and stays marked as factory if either entry was.

- **A rename that could not be saved now says so.** Renaming a disk in the
  browser showed the new name straight away even when it could not be saved,
  and the next rescan quietly took it back. Now the old name comes back at
  once, with a short notice that nothing was changed.

## v0.6.5 — 2026-09-28 — Renames and protection tabs survive a bad save

- **Saving a disk's details writes only the disk's own information to the
  catalogue.** Some of what the disk browser shows about a row, such as the
  folder it sits in, used to be saved into the catalogue along with the
  disk's names. It no longer is.

- **A damaged renames file no longer costs you your renames.** If the file
  that holds your disk renames was damaged, saving one more rename used to
  replace it, and every earlier rename was lost. The damaged file is now kept
  beside it under a name ending in `.unreadable-` and the date, and your new
  rename is saved. If the file cannot be read at all, nothing is written.

## v0.6.4 — 2026-09-28 — Filters sit where the Mirage puts them

- **In the default engine, every sound's filter now sits where the Mirage's
  own operating system puts it.** Where a sound's filter rests, and how far
  its envelope opens, used to sit a fixed step too bright on every sound, and
  ignored the filter offset each wavesample carries. They now follow OS 3.2's
  own rule, including each wavesample's Relative Filter Freq and its Maximum
  Filter Freq limit, so editing either is heard on the next note. Most sounds
  come out darker, some of them clearly. Sounds whose filter envelope opens
  fully sound the same. The LLE engine is unchanged.

## v0.6.3 — 2026-09-25 — A disk in your User Library is yours

- **A disk in your User Library is yours.** Copying a factory disk into the
  User Library used to make a second factory disk: protected, and protected
  together — write-protecting one protected both, and a copy that kept its
  name stayed "factory" after you saved to it. A library disk is now
  identified by where it is in the library, not by what it contains. It is
  writable until you protect it, protecting it never touches the original,
  and its label says what it was copied from — *copy of A1*, or *based on A1
  · modified* once you have saved to it. Its names follow the original's
  until you rename the copy itself, and a rename sticks across saves.
- **The MOUNTED mark follows the disk that is actually in the drive,** even
  when a User Library copy and its original share a filename.
- Moving a disk to another folder inside your library keeps its protection,
  names and lineage — whether the next rescan finds it or you load it
  first.
- If your library and Sound Disks folders overlap (or are the same
  folder), disks in the Sound Disks folder stay sound disks and keep
  their protection.
- The records live in `library.json` inside the User Library folder, so they
  move, sync and back up with it.
- A User Library disk you protected before this version comes up
  unprotected once. Protect it again and it stays protected.
- A User Library disk's names are edited on its label. DETAILS is for the
  disks in your Sound Disks folder.

## v0.6.1 — 2026-09-24 — Oversampling without the grit

The first release on the 0.6 line.

- Oversampled render quality now filters properly before it steps down to
  your project's sample rate. The filter it used barely touched anything
  above half the project rate, so the extra detail oversampling computes
  folded back into the audible range as grit. The new one removes it — by at
  least 50 dB, the 8-bit sound chip's own noise floor — while keeping the
  audible band flat to within a tenth of a decibel.
- Changing Render Quality while the instrument is playing is now safe. The
  change used to be applied from the interface while audio was being made;
  it now reaches the sound chip between audio blocks.

## v0.5.120 — 2026-09-23 — The filter at every sample rate

The last release on the 0.5 line.

- The filter now sits where the panel puts it at every sample rate. It had
  only ever been set up for 44.1 kHz, so everywhere else it ran too high: a
  project at 48 kHz played about a semitone and a half brighter than the panel
  said, one at 96 kHz more than an octave brighter, and Oversampled quality
  was brighter still at any rate, 44.1 kHz included. At 44.1 kHz in Standard
  and Direct nothing changes. **If your
  projects run above 44.1 kHz, DSKlusion will now sound darker than it did** —
  that is the filter returning to the setting on the panel.
- Switching Render Quality from Oversampled back to Standard or Direct no
  longer leaves the instrument playing two octaves low with slow envelopes.
  It happened the next time the host restarted its transport, changed its
  buffer size or re-activated the plugin.

### Both products

- Reopening a project now tells the host to re-read the plugin's parameters,
  so automation lanes and generic editors show the restored values instead of
  stale ones. CLAP hosts were the most affected.
- The window opens faster after the first time in a session. Every window in
  one DAW now shares a single browser profile instead of building a fresh one
  on each open, and closing a window no longer leaves a few megabytes behind
  on disk.
- Plugin scanners and validators now get a fully prepared plugin, rather than
  one that skipped its setup when it recognised them.

## v0.5.118 — 2026-09-22 — Notices, corrected

### Both products

- The third-party notices now state that ASIO support is part of every
  Windows build — VST3, CLAP and Standalone alike — and use Steinberg's
  current trademark wording.

## v0.5.117 — 2026-09-22 — Naming the keyboard button

### Both products

- The show/hide keyboard button in the header now carries its own name for
  screen readers instead of relying on its tooltip, which is never shown on a
  touch screen. The name follows the button, so it says "Hide keyboard" when
  the keyboard is up and "Show keyboard" when it is not.

## v0.5.116 — 2026-09-22 — Renaming, from the keyboard

- The disk title and the sound names in the browser can now be reached and
  renamed with the keyboard. They were click-only, and the only hint that
  they could be renamed at all was a tooltip — which never appears if you are
  not using a mouse. Each one now announces itself as a rename.

## v0.5.114 — 2026-09-22 — Settings and the disk list, from the keyboard

### Both products

- The option lists in Settings — engine mode, window scale, display style,
  theme — can now be reached and chosen with the keyboard, and a screen
  reader announces them as a group and says which option is selected. They
  were previously mouse-only, and selection was shown in colour alone.

## v0.5.113 — 2026-09-22 — The ASIO notice both products owed

### Both products

- The About dialog now carries the ASIO trademark notice. Mample and
  DSKlusion can both use ASIO audio drivers on Windows, and Steinberg's
  licence requires the notice wherever an About box credits anyone else.
  Mample's manual gains the same line, and lists ASIO among the components
  the plugin is built with.

## v0.5.108 — 2026-09-21 — Show Tour stops being a promise

- **The "Show Tour (Coming Soon)" placeholder is gone** from Settings →
  APPEARANCE. It had been sitting there promising a guided tour, and
  DSKlusion is not getting one — a button that says "coming soon" forever
  is worse than no button. Nothing else in that tab changes.

---

## v0.5.92 — 2026-09-16 — Two windows open at once no longer break the UI

- **Running a second window no longer blanks or crops the first's UI.** Each
  open editor now keeps its own private WebView data folder instead of one
  shared per product, so the standalone and the plugin — or two plugin
  instances in one project — can be open together on Windows without one
  coming up white or with its bottom cut off. Folders left behind by a
  closed instance are cleaned up automatically.

---

## v0.5.91 — 2026-09-16 — Built on JUCE 9.0.2

- **Built on JUCE 9.0.2**, up from 9.0.1.

---

## v0.5.90 — 2026-09-16 — A User Library for your own disks

- **A User Library folder for your own disks.** Settings → Sound has a new
  User Library row under Sound Disks. By default it is
  Documents\KnivesOnStrings\DSKlusion\User Library, and the disk browser
  creates it the first time it looks.
- **The disk browser lists your User Library first,** in its own group above
  your sound disks, subfolders included. A folder kept inside the other one is
  listed only once, and inserting a disk or restoring a backup finds it in
  whichever folder it came from.

---

## v0.5.89 — 2026-09-15 — MASOS Save Upper and Save Both verified

- **MASOS's Save Upper and Save Both are now tested** on a booted MASOS disk,
  like Save Lower and Save Configuration before them. Each writes the right
  sound to the slot you choose, marks that slot as used on the disk, and changes
  nothing else.

---

## v0.5.88 — 2026-09-15 — Write-protected disks stay protected

- **A write-protected disk now refuses saves**, as a real write-protected
  floppy does: the Mirage shows **Pd** and the disk is left unchanged. Until
  now, marking a disk write-protected in the browser was only recorded; the
  emulated drive never saw it.
- **Turning write protection on or off applies straight away** to the disk in
  the drive. For any other disk it applies when that disk is mounted.
- **Disks from the sound library come write-protected.** If you have been
  saving to one, turn its write protection off in the disk browser first.
  Factory, OS and commercial disks ask you to confirm twice.
- **Your own disks, which carry no write-protect mark, are writable**, and the
  browser now shows them that way.

---

## v0.5.87 — 2026-09-13 — Settings look the same everywhere

- **Help text in Settings now has one typeface and colour** in both
  products. Several of DSKlusion's rows (Boot ROM, OS disk images, sound
  disks, disk writes, audio and logging) had fallen back to a typewriter face.
- Folder and file rows share one design, and their Browse buttons match the
  other buttons in Settings.
- An empty folder or file row now reads "(default)" everywhere. Each of these
  settings falls back to a real default location, so "(not set)" was wrong.

---

## v0.5.86 — 2026-09-13 — LLE says when it needs the boot ROM

- **Choosing LLE without a boot ROM now tells you so.** DSKlusion stays on
  HLEv2 and says what is missing: no boot ROM where Settings says to look, or
  a file there that is not one. **Choose Boot ROM…** picks the file and starts
  LLE from it; **Use HLEv2** makes HLEv2 your engine.
- **Starting with LLE saved but no boot ROM runs HLEv2** and shows the same
  notice, rather than a Mirage that never boots. LLE stays your saved engine,
  so it starts once a boot ROM is in place. A boot ROM copied into the
  default folder while DSKlusion is open is found the next time LLE is chosen.
- Choosing an unusable boot ROM file while LLE is running switches to HLEv2
  with the same notice.

---

## v0.5.85 — 2026-09-13 — The standalone apps keep your settings

- **Settings chosen in the standalone apps are kept.** A folder chosen in the
  standalone Mample or DSKlusion (sound disks, OS disk images) could be gone
  the next time the app started, along with other settings changed in the same
  session: the app's own audio, MIDI and window state was saved over them. That
  state now has a file of its own, `Mample.standalone.settings` or
  `DSKlusion.standalone.settings`, and your audio device, MIDI inputs and
  window position carry over the first time the new version starts. A folder
  lost this way needs choosing once more.

- **Settings → Sound → Boot ROM** sets the file LLE mode boots the Mirage
  from. It defaults to `Documents\KnivesOnStrings\DSKlusion\Firmware\mirage.bin`,
  so a ROM placed there needs no setup; Browse picks a file anywhere else.
- The row tells you whether it found a usable ROM there. A Mirage boot ROM is
  exactly 4,096 bytes, and a file of any other size is named as the problem.
- Choosing a boot ROM while LLE is running restarts the machine from it.
- HLEv2, the default engine, does not use the boot ROM and does not need one.
  The Engine Mode description now lists what LLE needs: the boot ROM and an
  OS disk.

---

## v0.5.84 — 2026-09-12 — About links go somewhere, and credit the right people

- **The About box's buttons led nowhere.** Manual pointed at a page that did
  not exist, and GitHub at a private repository, so both failed for everyone
  who clicked them. Website and GitHub now open each product's own page and
  its public repository. The Manual button appears in Mample, which has a
  manual, and no longer appears in DSKlusion, which does not.
- **Credits link to the projects behind them**: JUCE, React, Tailwind CSS,
  Vite, the mc6809 CPU core, the HxC Floppy Emulator project, and each of the
  five typefaces. Links open in your web browser.
- **The mc6809 CPU core is now credited to its author.** It is elmerucr's MIT
  licensed MC6809. The About box and the Mample manual both named someone
  else.
- **The HFE credit now credits the format.** It read as though Virage used
  borrowed parsing code; Virage reads HFE disk images with its own code, and
  the format comes from the HxC Floppy Emulator project.
- The credit descriptions shortened in v0.5.83 are back in full. The About box
  scrolls when it needs to.

---

## v0.5.83 — 2026-09-12 — The About box credits the typefaces

- **Both products' About box now credits the fonts they ship.** Inter, Noto
  Sans Symbols 2, Noto Sans Math, Courier Prime and IBM Plex Mono are all used
  under the SIL Open Font License 1.1, which asks that its notice travel with
  the software. Mample's manual has named them since v0.5.78, but DSKlusion has
  no manual, so until now it credited them nowhere.
- **The About box said JUCE 8.** The plugins are built on JUCE 9.
- The credits were tightened so the whole About box fits Mample's window
  without scrolling, with every name and author kept.

## v0.5.79 — 2026-09-12 — One set of text sizes, across both products

- **Text is now set to a scale rather than to whatever looked about right.**
  Between them the two products wrote 257 font sizes by hand. Mample used 14
  different ones and DSKlusion 15, and on the main window each drew eight at
  once. The three doing nearly all the work sat within two pixels of each
  other, which is not a scale, and it is the reason nothing on either screen
  read as more important than anything else. There are now five steps, each
  named for the job it does, and a component asks for the job. Both windows
  render four of them plus the wordmark.
- **The disk browser had a second, invisible scale.** Nineteen of its sizes
  were set in half-pixels — 7.5, 8.5, 9.5, 10.5, 11.5 and 12.5 — alongside the
  whole-pixel ones. Those are gone.
- Nothing is clipped by the change. Every piece of text in both windows was
  measured against its box before and after, and none of it overflows.
- The product wordmarks keep their own sizes. They are a logo set in type, not
  a heading.

---

## v0.5.70 — 2026-09-11 — Stray pale lines where the page meets the window

- **The surface behind the page now matches the page.** The editor's own fill
  and the web view's background colour were a light grey in both products,
  lighter than anything at the top of either window, so any seam between the
  web view and the window hosting it read as a pale line. Both now match the
  header.

---

## v0.5.69 — 2026-09-08 — Opt-in telemetry and an in-plugin issue reporter, compiled out by default

- **Opt-in telemetry and an in-plugin issue reporter, both compiled out by
  default.** Ported from the shared plugin boilerplate as one library both
  products link. When a build enables them, anonymous session data is sent only
  after you have been asked once and said yes — never audio, never your samples,
  never anything that identifies you — and "Report an Issue…" in About opens a
  pre-filled form, or hands you a copyable URL if it cannot reach the server.
  Turned **off** in every build shipped so far.

---

## v0.5.66 — 2026-09-07 — A 400+ disk catalogue, content-hash recognition, and one shared engine across both products

Everything since v0.4.12 (2026-08-16), consolidated.

- **A bundled disk catalogue of 400+ disks.** Mount a disk from the definitive
  archive and it is identified by name, OS, and what is actually on each half.
  Recognition is by **content hash**, not filename, so a disk still identifies
  correctly if it has been renamed, has no extension at all, or arrived as a
  Gotek-style numbered file. `.edm` container images load natively, and a file
  that genuinely is not a Mirage disk is reported as invalid instead of being
  loaded as garbage.
- **Disk metadata is editable.** Wavesamples, key ranges and program names can
  all be edited against the full schema, and curation done locally can be
  harvested back into the shipped catalogue rather than living only on your
  machine.
- **Disks in HFE and EDM containers boot in HLEv2 mode** on both products, and a
  disk load now reaches sounds 2 and 3 instead of being hard-wired to lower/upper
  1. The sample loop window is armed from the P63:P64 pair rather than the
  sample-end page, which is what the hardware does.
- **The on-screen keyboard no longer misses note releases.** Pointer capture was
  reworked; a key you slide off no longer sticks on.
- The keyboard is half its old height on both products, and the waveform panels
  are about 30% smaller, so more of the window is the thing you came for.

- **You can save a disk back out to a file.** Until now a mounted image was
  strictly read-only from your side: the firmware could write to it, but there
  was no way to keep the result. There is now a save gesture that writes the
  mounted image out to a real file, so a disk you have sampled to, renamed or
  re-parametered survives the session.
- **It backs up before it overwrites, and it will not delete anything it did
  not create.** Overwriting an existing image writes a backup alongside it
  first, and the backups are reachable rather than hidden somewhere you have to
  go looking. A destructive firmware write asks first.
- **Write protection is honoured for real.** The WD1772 controller reports the
  write-protect state and the firmware refuses the write itself, the way the
  hardware does — rather than the UI pretending the disk is locked while the
  emulation happily writes anyway.
- **A floppy disk browser.** Browse the catalogue, see what is on a disk before
  mounting it, and rename as you go — the rename flow advances by itself, and an
  "Unnamed" facet collects the disks still needing a name. The detail panel fits
  inside the plugin window rather than overflowing it.
- **Your disk names are promoted into the shipped catalogue**, so naming work
  done locally becomes part of the bundled data rather than being lost on
  reinstall.
- **Parameters know which OS you booted.** OS 3.2, MASOS and SP each have their
  own parameter definitions, and the parameter drawer reacts to whichever one is
  running — with live reads alongside the disk's own baseline, and cards that
  bold the values which differ from what the disk shipped with.
- **RESET is a real power cycle** — it reboots the mounted disk rather than
  half-resetting into an inconsistent state, and it waits for the drive to go
  genuinely quiet before swapping rather than trusting a fixed delay. A reboot
  glyph on the disk pill replaces the old header RESET button.
- **A KEYS tab** documenting the numpad-to-Mirage front-panel mapping, generated
  from the live binding map so it cannot drift from what the keys actually do.
  The numpad operators (`/ * + -`) drive PARAM / VALUE / ON / OFF.
- **iPad layout.** The UI scales to fit, the keyboard is sized for touch, and the
  parameters open in a drawer instead of a modal that ran off the bottom of the
  screen.
- The HLEv2 front panel's LOAD LOWER / LOAD UPPER plus a digit loads sounds 2
  and 3 correctly.
- Front-panel polish: the CONTROL / SELECT / SEQ / LOAD / SAMPLE groups line up
  at matching heights, the keyboard and mod wheel no longer overlap, and the
  canvas is pinned to a true 4:3.

