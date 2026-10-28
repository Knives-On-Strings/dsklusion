## v0.7.4 — 2026-10-27 — HLEv2 panel display fixes

- **Fixed:** In HLEv2, LOAD LOWER and LOAD UPPER now show LL or LU, then the sound number; pressing both, in either order, shows LA and loads both halves.
- **Fixed:** In HLEv2, the display rests on 21 once a sound is loaded and flashes nd with no disk, instead of staying blank.
- **Fixed:** In HLEv2, the "Booting Firmware" overlay no longer appears.

## v0.7.3 — 2026-10-26 — Mample's KoS look, Hi-viz theme, redrawn browsers

- **New:** Both disk browsers get a quieter look: Graphite keys instead of amber, a LIBRARY (n) count, and a Current: line.
- **New:** A ☰ menu in the browsers holds Hide duplicates and label export and import. Hide duplicates is turned on for everyone in this version, even if you had turned it off; switch it off again if you like.
- **New:** Recent shows the last 10 disks you loaded, kept across restarts.
- **New:** The header has a stereo VU meter.
- **New:** The waveform screens light each wavesample while it plays. Under MASOS or Sound Process in the LLE, no wavesamples light.
- **Improved:** Rescan is now an icon, and tags are one flat list you can filter by.
- **Improved:** Settings → Appearance is laid out as a grid in both products.
- **Improved:** The tours are updated and show once more.
- **Improved:** The User Library now lives inside the Mirage_Disks folder, and both products share its protect and rename records.
- **Improved:** Disk catalogue 2.8: corrected disk names now reach existing installs.
- **Improved:** Release packages are named with their platform and architecture, such as win-x64 or mac-universal.

- **New:** A Hi-viz theme for low vision: Settings → Appearance → Theme.
- **New:** The browser shows a redrawn floppy, with EJECT, the disk window and SAVE DISK underneath. The disk star stars every half.
- **New:** The disk in the drive is marked Inserted, in the list and on the floppy.
- **New:** Show: All, Unnamed or Write-protected, and Sort by Name, Date added, Last inserted or Directory.
- **Improved:** Keypad panels are 510 px wide in every skin, and the mk1 keys are narrower.
- **Improved:** The User Library moved to Mirage_Disks\User Library, shared with Mample. If you saved disks in v0.7.2, DSKlusion shows where they are and where to move them.
- **Improved:** Render quality is remembered.
- **Fixed:** In the sample dialog, Tab skips the Raw PCM fields unless a raw file is chosen.
- **Fixed:** DSKlusion restores the last disk: an LLE project reopens with its OS booted and the sound disk back in the drive, and the browser remembers a disk mounted from it.

## v0.7.2 — 2026-10-23 — DSKlusion's new look, tours and a faster browser

- **New:** The disk browser opens at once with the last list it showed, then refreshes in place.
- **New:** A Rescan button in the disk browser re-reads your library on demand.
- **Improved:** Both products keep sound disks in one shared folder, Documents\KnivesOnStrings\Mirage_Disks, by default.

- **New:** Panel skins in Settings → Appearance → Panel: KoS, mk1, mk2, mk3 and mk4.
- **New:** A light theme: Settings → Appearance → Theme. The front panel keeps its hardware colours.
- **New:** Green LCD and Green LED displays. Settings → Appearance → Display matches the panel skin by default (amber on KoS and mk1, Green LED on mk2, green LCD on mk3 and mk4), or can be set to Classic Amber, OLED Blue, Green LCD or Green LED for every skin.
- **New:** An engine band across the top of the panel shows the engine, and in LLE the firmware and OS, at a glance.
- **New:** A MIDI light and a Params key in the header.
- **New:** A short first-run tour, which Show Tour in Settings → Appearance runs again.
- **New:** Optional usage data, an update check and Report an Issue, as in Mample. You choose in Settings → Privacy, and DSKlusion asks before sending any usage data.
- **Improved:** A new look for DSKlusion's default KoS panel: soft raised keys on one panel, mixed-case labels, LOAD stacked above SAMPLE in two tones, and a recessed display with faint unlit segments. The header and the waveform screens share the look.

## v0.7.1 — 2026-10-23 — Mono mode, voice reuse, LLE filter tuning

- **New:** Mono mode (P29) plays as on the Mirage: one voice per keyboard half, the lowest held key wins, and a lower key changes pitch without restarting the note (legato).
- **Improved:** A key struck again while its note still rings restarts on that same voice, as the Mirage does.
- **Improved:** Mac and Windows now render identically.
- **Fixed:** Resonance (P37) now matches DSKlusion's LLE engine, so resonant sounds are stronger than before.

- **Improved:** Editing P29 on the panel restarts voice order, as the Mirage does.
- **Fixed:** In LLE, the boot filter auto-tune now tunes each filter, so LLE sounds have the same brightness as the default engine. LLE takes about 2 s longer to boot.

## v0.7.0 — 2026-10-22 — The Mirage's real clock, and HLEv2 matched to it

- **New:** A Note Timing setting: Tight (the default, unchanged) or Authentic, which adds the Mirage's own note-on and note-off delays.
- **Improved:** Voices are allocated as on the Mirage: a released, still-ringing voice is reused before a held note is cut, and a held one-shot frees its voice when its sample ends.
- **Improved:** Two-layer sounds start their second layer with the Mirage's own small delay, so velocity responds as on the hardware.
- **Improved:** Envelope and LFO rates follow the Mirage's measured clock, about 1–2% slower than before.
- **Fixed:** Envelope decays and releases follow the Mirage's ROM. Long tails were up to about a third too long.

- **Improved:** In LLE, the 6809 runs at 1 MHz as on a real Mirage, while the VIA and MIDI stay at 2 MHz. Boot, disk and other CPU-timed delays now take their real time; pitch is unchanged.
- **Improved:** Opening a disk and refreshing the waveform wait up to 20 s, to cover real-speed disk loading.
- **Fixed:** In LLE, MIDI could stop responding for good after one receive overrun.
- **Fixed:** Two DSKlusion LLE instances no longer share floppy rotation or sample-bank state.

## v0.6.73 — 2026-10-20 — Stereo, a tidier browser, and ASIO

- **New:** The disk browser can hide duplicate disks: identical copies show once, with a count.
- **New:** Tags in one set of chips, in both views: pick a family (Keys, Strings, Brass & wind, Synth, Percussion, Voice) to see the tags inside it.
- **New:** Disks and sounds with no tags get automatic tags from their names. They look dimmer, and you can remove any of them.
- **New:** The browser remembers its view, filters and last disk.
- **New:** The Windows Standalone apps support ASIO audio drivers.
- **Improved:** The library is no longer rescanned after a DAW restart; only new or changed disks are read.
- **Improved:** On Windows, "Install for me only" installs for the signed-in user and no longer asks for administrator rights.
- **Fixed:** A disk of your own named like a factory disk no longer shows that factory disk's names and sounds.
- **Fixed:** Your labels stay with a disk when you save over it.
- **Fixed:** Eight factory sound names now close their quotes, as in Low Voices "AH".

- **Fixed:** In LLE, system settings and instrument globals edited in the parameter drawer now stay put.

ASIO is a trademark of Steinberg Media Technologies GmbH, registered in Europe and other countries.

## v0.6.71 — 2026-10-20 — DSKlusion Windows installer

- **New:** A Windows installer for the VST3, CLAP and Standalone, with the licence to accept and the WebView2 Runtime if it is missing. No Ensoniq software is included.

## v0.6.70 — 2026-10-20 — Parameter ranges match the Mirage

- **Fixed:** Pitch Bend Range (P22) stops at 12, as on the Mirage. A session saved with a higher value reopens at 12.
- **Fixed:** A 2-sided HFE disk image loads from the right tracks instead of showing as damaged.

- **New:** P91 and P92 can be set from the host, and in HLEv2 from the front panel; Save Configuration (P14) keeps them.
- **Fixed:** MIDI Function Enable (P84) has the Mirage's four settings, 0–3, and starts at 2.
- **Fixed:** Internal Clock Rate (P87) runs 0–99 and starts at 48, as on the Mirage. High values no longer wrap.
- **Fixed:** In HLEv2, a setting changed from the parameter drawer, such as the MIDI channel (P82), stays changed on the front panel.
- **Fixed:** In LLE, the parameter drawer shows the Mirage's own Local On/Off (P30), and changing it reaches the instrument.
- **Fixed:** In LLE with MASOS or Sound Process booted, editing or automating a parameter no longer writes into an unrelated setting, such as MASOS's MIDI Omni.

## v0.6.69 — 2026-10-19 — Save your setup in HLEv2

- **New:** In HLEv2, Save Configuration Parameters (PARAM 14) saves your setup to the disk in the drive, as on the Mirage.

## v0.6.68 — 2026-10-19 — The Mirage's own digits; the panel reads back setup values

- **Fixed:** In HLEv2, the front panel shows the real value of Local, the MIDI settings and the sampling setup (P73–P77), and UP/DOWN steps from it instead of from 0.

## v0.6.63 — 2026-10-18 — Wrong-sized disk images are refused

- **Fixed:** A disk image file that is too short or too long to be a whole Mirage disk no longer loads, and the status line says so, giving its size.

## v0.6.58 — 2026-10-17 — Browse by sound, audition before loading, and update checks

- **Improved:** Every network request Mample makes now carries the same fixed headers, naming only KosNet and its version, never your DAW, operating system or language.

- **Improved:** In HLEv2, saving to a write-protected disk now waits as long as the Mirage does before flashing Pd.

## v0.6.57 — 2026-10-17 — A volume readout, and held loops that follow their loop point

- **New:** Hovering, dragging or focusing the VOLUME knob shows its level, for example "75 % −7.5 dB". Double-click returns it to the default, and the arrow keys adjust it once it has focus.
- **Improved:** The disk catalog names London 1's six drum kits and titles London 1 and 3.
- **Fixed:** A wavesample whose loop switch is stored as any value other than 0 or 1 now loops, as on the Mirage, instead of playing once (Factory Disk OS 3.2, Upper sound 2, wavesample 6).

- **Fixed:** In HLEv2, a held note now follows a loop end you move further out while it plays, as on the Mirage.

## v0.6.56 — 2026-10-17 — Saving sounds in HLEv2; Mample's default volume is 75%

- **Improved:** The master volume's soft clipping is smooth at both limits, and its added colour is the NE570's own 0.4%, so loud sounds distort far less.
- **Improved:** The disk catalog adds 28 disks (K-Muse L.A., Sound Cells, Minotaur and the self-oscillating filter OS) and names 122 sounds, including K-Muse London 4.

- **New:** In HLEv2, save a sound from the panel as on the Mirage: PARAM 11, 12 or 13, a slot digit, then ENTER. The display flashes and blanks with the Mirage's timing, shows Pd on a write-protected disk and nd with no disk.
- **New:** SAVE DISK and its modified dot work in HLEv2, and a panel save writes the disk file after a backup, as in LLE.
- **Fixed:** In HLEv2, editing a wavesample's start, end, loop or loop switch (P60 to P65) now does what the Mirage does, including the other values it changes, so the sound plays and saves as on the hardware.
- **Fixed:** In HLEv2, a held note keeps sounding while you edit its loop points.
- **Fixed:** After a loop-point edit, the editor and your DAW show every value the edit changed, and undo restores them together.

## v0.6.53 — 2026-10-15 — LED-font readouts

- **Improved:** The About box credits the DSEG7 Classic typeface.

## v0.6.50 — 2026-10-14 — Favourites, tags and LED readouts

- **New:** Star a sound half in the disk browser and show only your ★ Favourites; stars are yours alone, shared between Mample and DSKlusion, and never exported.
- **New:** The catalog now tags 429 sounds by type (keys, strings, brass & wind, synth, percussion, voice), so you can filter the factory and third-party libraries by tag.

## v0.6.48 — 2026-10-14 — Shorter release notes

- **Improved:** Release notes are shorter and tagged New, Improved or Fixed, so they are quicker to scan.

## v0.6.45 — 2026-10-13 — Validation passes; sample loading fixed

- **Improved:** Passes clap-validator and pluginval (strictest level) in both products.
- **Fixed:** Pitch Bend's displayed value drifted when a host stored it as text.

- **Fixed:** The sample-load dialog's Load button stayed disabled on a fresh instance; sampling parameters P73–P77 now start at the Mirage's own boot values.

## v0.6.43 — 2026-10-13 — Damaged disk images flagged

- **Improved:** A damaged disk image still loads, and the status line names what is missing or unreadable.
- **Fixed:** In HLEv2, a disk with out-of-range system settings, such as a master tune above 99, no longer detunes every voice.

- **Improved:** A damaged disk mounts write-protected, so the Mirage can't save to it.
- **Fixed:** WINDOW SCALE resizes correctly in hosts that scale plug-in windows, such as Ableton Live.

## v0.6.42 — 2026-10-12 — Out-of-range notes; velocity values

- **Improved:** In HLEv2, notes outside the Mirage's keyboard (36–96) fold by octave onto the key the Mirage plays, with retrigger and sustain per note.
- **Fixed:** Velocity parameters P45/P46/P48/P49 and P55/P56/P58/P59 keep their full value through edits, undo, copy and save.
- **Fixed:** The amp release's velocity shift (P59) works as on the Mirage.

## v0.6.41 — 2026-10-12 — 32 tags per sound half

- **Improved:** A sound half can carry up to 32 tags; ADD CATALOG TAGS adds only those that fit.

## v0.6.40 — 2026-10-12 — Sound tags and your labels

- **New:** Tag each half of a sound in the disk library's editor: up to 16 tags of 64 characters, with suggestions. **Apply to both halves** copies them across.
- **New:** Tags and program names are kept in your own labels file, `disk_catalog.user.json`, which wins over the catalogue.
- **New:** Search matches tags, and clicking a tag filters the library by it.
- **New:** **EXPORT MY LABELS…** saves your labels to a file you can send us for the shared catalogue: content IDs and labels only, no file names or user names.
- **New:** Where a name differs from the catalogue's, the editor shows "Catalog: <name>"; **USE** restores it.
- **New:** **ADD CATALOG TAGS (n)** adds the catalogue's tags a half lacks; a **+tag** chip adds one.
- **Improved:** Names and tags you give a disk show in both products.
- **Improved:** Catalogue updates rename and retag only what you haven't changed yourself.
- **Improved:** The shipped catalogue is version 2.4.
- **Improved:** A disk without a content ID can't take tags or program names, and the editor says so.
- **Improved:** When labels can't be saved, the library says so and puts back what wasn't kept.

- **New:** A tagged sound appears under the sound-type chip its tags name; untagged sounds are still sorted by name.
- **Improved:** Program names edited in DETAILS are kept in your labels file.

## v0.6.39 — 2026-10-11 — OS MIDI setting shown

- **New:** Settings → MIDI shows the Mirage OS's own omni and channel (P81/P82), read-only, and warns in LLE when the OS would ignore notes.
- **Fixed:** Under MASOS, the on-screen keyboard plays on MASOS's own MIDI channel.

## v0.6.37 — 2026-10-11 — Mix mode and Keyboard Balance

- **Fixed:** In HLEv2 with mix mode on (P28), each key plays the Mirage's wavesample pair, fixing piano and MELPRO sounds.
- **Fixed:** Keyboard Balance (P24) balances the two halves as on the Mirage.
- **Fixed:** Relative Amplitude (P69) sets levels exactly as on the Mirage.
- **Fixed:** A mix-mode sound's second layer plays at the first layer's P69 level, changing about 20 library sounds.

## v0.6.36 — 2026-10-11 — One master tune and bend range

- **Fixed:** In HLEv2, master tune, bend range, velocity curve, balance and link (P21–P25) and P78–P80 are one setting for the whole instrument, as on the Mirage.
- **Fixed:** In HLEv2, the pitch wheel's range follows P22.
- **Fixed:** In HLEv2, MIDI controllers 2–7 and channel pressure work where a sound assigns them (P78/P79).
- **Fixed:** The editor sizes correctly under Ableton Live's plug-in auto-scale.

- **Fixed:** In LLE, the pitch wheel rests exactly on centre.

## v0.6.35 — 2026-10-11 — Key-scaled decay; two-layer mix

- **Fixed:** In HLEv2, decay scales by key (P47/P57), so higher notes decay faster on about 20% of library sounds.
- **Fixed:** In HLEv2, two-layer programs mix as on the Mirage: by mod wheel at P35 = 0, by velocity above 1.
- **Fixed:** In HLEv2, the second layer stays audible at its quietest level instead of going silent.

- **Fixed:** Undo, redo, copy and keypad edits keep P47/P57's exact value.

## v0.6.34 — 2026-10-10 — Per-half LFO

- **Fixed:** In HLEv2, each half vibratos with its own LFO speed and depth (P31/P32).
- **Fixed:** In HLEv2, the LFO no longer moves the filter, so vibrato sounds may change slightly.
- **Fixed:** In HLEv2, the second layer keeps its vibrato and pitch bend through the release.
- **Fixed:** In HLEv2, LFO edits apply from the next note, as on the Mirage.

## v0.6.33 — 2026-10-10 — SAVE DISK writes the right disk

- **Fixed:** SAVE DISK saves the disk that was in the drive when you started, even if you change disks while the dialog is open.
- **Fixed:** The disk-write confirmation describes the disk actually in the drive, and writes only to that disk.
- **Fixed:** Toggling write-protect on two disks in a row no longer loses the first toggle.
- **Fixed:** A write-protect toggle the drive refuses shows an error.

## v0.6.31 — 2026-10-10 — VOLUME knob on older macOS

- **Fixed:** The controls load on older macOS versions.

---

## v0.6.30 — 2026-10-10 — Safe LLE sample loads

- **Fixed:** In LLE, loading a sample can no longer leave the sound or waveform half old, half new; the waveform may lag by about a second.
- **Fixed:** In LLE, a LOAD SAMPLE made before audio is running shows "Sample load pending -- start audio and try again" instead of "Error".
- **Fixed:** In LLE, editing a wavesample or program other than the selected one now changes the sound.
- **Fixed:** SAVE DISK with no disk in the drive saves nothing.

- Internal improvements.

## v0.6.29 — 2026-10-10 — macOS minimum per Mac

- **Improved:** The installers and Mample manual state the macOS minimum: 10.15 on Intel Macs, 11 on Apple Silicon.

## v0.6.28 — 2026-10-10 — Held mod wheel survives LOAD

- **Fixed:** In HLEv2, a held mod wheel keeps its effect after a LOAD or a sample load.

## v0.6.27 — 2026-10-09 — HLEv2 edits change the sound

- **New:** In HLEv2, the drawer shows edited parameters in bold.
- **Fixed:** In HLEv2, every parameter edit, from the drawer, waveform, undo, copy or panel keys, changes the sound. Not yet: DAW automation, or edits saved with your project.
- **Fixed:** In HLEv2, a loaded sample is the one you hear and see.
- **Fixed:** In HLEv2, LOAD keeps the other half's edits.
- **Fixed:** HLEv2 no longer changes samples stored in LLE's memory.
- **Fixed:** In LLE, a parameter edit no longer clicks or cuts a loop.
- **Fixed:** Dropouts in some hosts, in either engine.

## v0.6.25 — 2026-10-09 — Tighter MIDI; clean releases

- **Fixed:** In HLEv2, re-striking a held or sustained key, or a doubled controller, could leave a note sounding.

## v0.6.24 — 2026-10-09 — Top Key keeps to the keyboard

- **Fixed:** P72 Top Key ranges 1–61, as on the Mirage, and defaults to 61.

## v0.6.23 — 2026-10-09 — Hex parameters shown in hex

- **Improved:** In HLEv2, the panel shows and takes P60–P64, P66, P68, P97 and P99 as two hex digits, as OS 3.2 does.

## v0.6.22 — 2026-10-08 — Fine tune uses its full range

- **Fixed:** P68 Fine Tune uses the Mirage's full 0–255 range, shown in hex. Factory sounds keep their pitch.

## v0.6.19 — 2026-10-08 — Mac disk-image installer

- **New:** On macOS, each product ships as a signed, notarized disk image with its installer, read-me, licences and uninstaller.
- **Fixed:** The licence agreement no longer opens with an internal draft note.

## v0.6.18 — 2026-10-07 — Contact addresses

- **Improved:** The licence and Mample manual give our legal@, privacy@, support@ and hello@knivesonstrings.com addresses; bug reports still go to GitHub issues.

## v0.6.17 — 2026-10-07 — macOS 10.15 Catalina

- **Improved:** Both products run on macOS 10.15 Catalina on Intel Macs (Apple Silicon needs macOS 11); keep Safari up to date there.

## v0.6.16 — 2026-10-07 — Internal tooling

- **Improved:** The Mample manual gives hello@knivesonstrings.com for general questions.

## v0.6.15 — 2026-10-06 — One floppy drive for both engines

- **Improved:** HLEv2 and LLE share one floppy drive; in HLEv2, mounting a disk loads nothing unless nothing is loaded yet.
- **Improved:** In HLEv2, LOAD LOWER or LOAD UPPER loads that half only, from the disk in the drive, and shows "nd" with no disk.
- **Improved:** Switching engines and RESET keep the disk in the drive, including anything the Mirage wrote to it.
- **Fixed:** The disk browser's hint is the same in both engines.

## v0.6.14 — 2026-10-05 — Mample Windows installer; no ASIO

- **New:** The About box says "Beta Tester Version".
- **Improved:** The Windows standalone apps use WASAPI or DirectSound; ASIO is no longer supported. Plug-ins are unaffected.

- **Fixed:** Opening a disk just as another load finished could briefly show the Booting Firmware overlay or a stale waveform.

## v0.6.13 — 2026-10-04 — Mample network fixes

- **Improved:** DSKlusion still makes no network connections, and every build is now checked for it.

## v0.6.12 — 2026-10-03 — Mid-load mounts reported correctly

- **Fixed:** In LLE, mounting a disk during a load could report a failure even when the disk went in.

## v0.6.11 — 2026-10-03 — Panel saves reach your files

- **New:** In LLE, a save on the Mirage's panel writes the disk back to its file, after backing it up, even with the window closed. HLEv2 follows later.
- **New:** A disk that can't be written back, such as an `.hfe` or `.edm`, asks where to save a copy, which then replaces it in the drive.
- **Improved:** Saves reach the right file across disk changes, and one that reaches no file is reported.
- **Improved:** Restoring a backup of the disk in the drive asks you to eject it first.
- **Improved:** The SAVE DISK dot stays lit until a save reaches the disk's file.
- **Fixed:** Open Disk in LLE loads both halves of a sound, and sooner.
- **Fixed:** The waveform shows the sound you just opened, not the old one.
- **Fixed:** Frequent saves of one disk in a day could lose the backup just taken.

## v0.6.9 — 2026-09-30 — Per-disk backups

- **Improved:** Moving or renaming a disk inside your User Library takes its backups with it.
- **Improved:** A restore first backs up what it replaces, so it can be undone.
- **Fixed:** Two disks with the same name shared one backup list and couldn't be restored; each now has its own.
- **Fixed:** Existing backups move to their own disk's list; none is deleted.
- **Fixed:** A damaged backup record no longer loses your backup history; it is kept aside, named `.unreadable-` and the date.

## v0.6.7 — 2026-09-30 — Repeatable LLE boots

- **Fixed:** The LLE engine boots the same way every time.

## v0.6.6 — 2026-09-29 — Damaged catalogue kept

- **Fixed:** A disk catalogue that can't be read is never saved over, so your names and protection tabs can be recovered.
- **Fixed:** Merging duplicate catalogue entries for a disk keeps it protected if either was.

- **Fixed:** A rename that can't be saved reverts at once, with a notice.

## v0.6.5 — 2026-09-28 — Renames survive a bad save

- **Fixed:** Saving a disk's details writes only the disk's own information to the catalogue.

- **Fixed:** A damaged renames file no longer loses your renames; it is kept aside.

## v0.6.4 — 2026-09-28 — Filters sit where the Mirage puts them

- **Fixed:** In HLEv2, filters sit where OS 3.2 puts them, honouring each wavesample's Relative and Maximum Filter Freq; most sounds are darker. LLE is unchanged.

## v0.6.3 — 2026-09-25 — User Library disks are yours

- **Improved:** A disk copied into your User Library is yours: writable until you protect it, labelled *copy of A1*, and named like the original until renamed.
- **Improved:** A library disk keeps its protection, names and lineage when moved within the library; protect older ones once more.
- **Improved:** Disks in the Sound Disks folder keep their protection even when it overlaps your library.
- **Fixed:** The MOUNTED mark follows the disk actually in the drive.

## v0.6.1 — 2026-09-24 — Clean oversampling

- **Fixed:** Oversampled render quality no longer adds grit: aliasing is at least 50 dB down.
- **Fixed:** Changing Render Quality while playing is now safe.

## v0.5.120 — 2026-09-23 — The filter at every sample rate

- **Fixed:** The filter sits where the panel puts it at every sample rate. **Projects above 44.1 kHz will sound darker.**
- **Fixed:** Leaving Oversampled quality no longer drops the instrument two octaves.

- **Improved:** The window opens faster after the first time in a session, and closing it leaves no files behind.
- **Fixed:** Reopening a project shows the restored parameter values in the host, notably in CLAP hosts.
- **Fixed:** Plug-in scanners and validators get a fully prepared plug-in.

## v0.5.118 — 2026-09-22 — Notices, corrected

- **Fixed:** The third-party notices state ASIO support correctly.

## v0.5.117 — 2026-09-22 — Naming the keyboard button

- **Fixed:** Screen readers name the show/hide keyboard button "Show keyboard" or "Hide keyboard".

## v0.5.116 — 2026-09-22 — Renaming, from the keyboard

- **Improved:** Disk titles and sound names can be renamed from the keyboard.

## v0.5.114 — 2026-09-22 — Keyboard access to Settings

- **Improved:** Settings option lists work from the keyboard and with screen readers.

## v0.5.113 — 2026-09-22 — ASIO notice

- **Fixed:** The About box carries the ASIO trademark notice.

## v0.5.108 — 2026-09-21 — Mample guided tour

- **Improved:** The "Show Tour (Coming Soon)" placeholder is gone.

---

## v0.5.92 — 2026-09-16 — Two windows at once

- **Fixed:** On Windows, a second open window no longer blanks or crops the first.

---

## v0.5.91 — 2026-09-16 — Built on JUCE 9.0.2

- **Improved:** Built on JUCE 9.0.2.

---

## v0.5.90 — 2026-09-16 — A User Library for your own disks

- **New:** A User Library folder for your own disks, by default Documents\KnivesOnStrings\DSKlusion\User Library (Settings → Sound), listed first in the disk browser.

---

## v0.5.89 — 2026-09-15 — Internal improvements

- Internal improvements.

---

## v0.5.88 — 2026-09-15 — Write protection enforced

- **Improved:** Library disks come write-protected, and factory, OS and commercial disks ask twice before you unprotect them. Your own disks are writable.
- **Fixed:** A write-protected disk refuses saves, and the Mirage shows **Pd**.

---

## v0.5.87 — 2026-09-13 — Consistent Settings

- **Improved:** Settings rows look the same in both products.

---

## v0.5.86 — 2026-09-13 — LLE asks for its boot ROM

- **Improved:** Without a usable boot ROM, LLE falls back to HLEv2 and says what is missing, offering **Choose Boot ROM…** or **Use HLEv2**.

---

## v0.5.85 — 2026-09-13 — Standalone settings kept

- **Fixed:** The standalone apps keep the settings you choose; a folder lost this way needs choosing once more.

- **New:** Settings → Sound → Boot ROM sets the file LLE boots from, by default `Documents\KnivesOnStrings\DSKlusion\Firmware\mirage.bin`, and says whether it is usable.
- **Improved:** The Engine Mode description lists what LLE needs: the boot ROM and an OS disk.

---

## v0.5.84 — 2026-09-12 — About box links and credits

- **Improved:** Credits link to the projects behind them.
- **Fixed:** The About box's Website, GitHub and Manual buttons open real pages; Manual appears only in Mample.
- **Fixed:** The mc6809 CPU core is credited to its author, and the HFE format to the HxC Floppy Emulator project.

---

## v0.5.83 — 2026-09-12 — Typeface credits

- **Improved:** The About box credits the shipped fonts: Inter, Noto Sans Symbols 2, Noto Sans Math, Courier Prime and IBM Plex Mono.
- **Fixed:** The About box names JUCE 9, not JUCE 8.

## v0.5.79 — 2026-09-12 — One type scale

- **Improved:** Text in both products follows one five-step type scale.

---

## v0.5.70 — 2026-09-11 — No pale edge lines

- **Fixed:** No pale seam where the page meets the window.

---

## v0.5.69 — 2026-09-08 — Opt-in telemetry, switched off

- **New:** Opt-in telemetry and an issue reporter, switched off in every build so far. When on, nothing is sent until you agree, and never audio or samples.

---

## v0.5.66 — 2026-09-07 — Disk catalogue and one shared engine

- **New:** A bundled catalogue of 400+ disks recognises each disk by its content, even renamed or Gotek-numbered.
- **New:** `.edm` images load, and HFE and EDM disks boot in HLEv2.
- **New:** Disk metadata (wavesamples, key ranges, program names) is editable.
- **Improved:** A file that isn't a Mirage disk is reported as invalid.
- **Improved:** The keyboard is half its old height and the waveform panels about 30% smaller.
- **Fixed:** Disk loads reach sounds 2 and 3.
- **Fixed:** A key you slide off the on-screen keyboard no longer sticks.

- **New:** Save a mounted disk to a file, with a backup before any overwrite; a destructive firmware write asks first.
- **New:** A floppy disk browser: see what is on a disk before mounting it, and rename as you go.
- **New:** Parameters follow the booted OS (OS 3.2, MASOS or SP), and values that differ from the disk show in bold.
- **New:** A KEYS tab maps the numpad to the front panel.
- **New:** An iPad layout: the UI scales to fit, and the keyboard is sized for touch.
- **Improved:** RESET is a real power cycle, from a reboot glyph on the disk pill.
- **Improved:** Your disk names join the shipped catalogue.
- **Fixed:** Write protection is honoured.

