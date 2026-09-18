# Virage Changelog

Shared changelog for **DSKlusion** (full hardware emulation, internally `MirageV`)
and **Mample** (sample-disk player). Entries under `### Shared` apply to both;
the per-product sections carry what only affects one of them.

Published to the two public repos and to knivesonstrings.com by
`tools/publish-changelogs.py` in the KoS company repo.

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

## v0.5.85 — 2026-09-13 — The standalone apps keep your settings, and choose where the Mirage boot ROM lives


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

## v0.5.70 — 2026-09-11 — The white line under Mample's keyboard


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
