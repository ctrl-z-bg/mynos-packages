# zxspectrum

A ZX Spectrum 48K, in a window: MyNOS's own emulator, written in OCaml
(MIT), with the Spectrum's ROM (Amstrad's permission: ROM-LICENSE).

```
mynos:/$ pkg install zxspectrum
mynos:/$ zxspectrum glazx             a game that comes with it
mynos:/$ zxspectrum /disk/roms/zx/game.tap
```

**Games that come with it** (in `/disk/pkg/zxspectrum/games`, named
without their extension): `glazx`, GLAZX (Eugeny Novikov, 2019, MIT), an
arcade duel for two at one keyboard (W A S D and F; I J K L and O); `snake`, Snake (David Crespo, 2020, MIT), for one player (1 to 9
the speed, Enter, then W A S D). Their licences and notes are beside
them.

**Other games and ROMs.** Nothing proprietary is needed: the Spectrum's
ROM comes with the package (Amstrad allows it to be given with an
emulator: `ROM-LICENSE`). Tapes (`.tap`) and snapshots (`.z80`, `.sna`,
of a 48K) of your own: copy them to `/disk/roms/zx/` (not into
`/disk/pkg/zxspectrum`, which `pkg` empties when it updates the
package) and give the path. Many free ones are on
https://spectrumcomputing.co.uk; `.tzx` tapes are not read.

A `.tap` loads at once (its blocks given to the ROM's loader), after the
machine has typed `LOAD ""` itself; `.sna` and `.z80` snapshots (48K)
load as they are. Without a file, the Spectrum's BASIC: `P` in K mode is
`PRINT`, as on the machine.

**Keys.** Letters, digits, Enter, Space; Shift and a letter: CAPS SHIFT
and it; Ctrl and a letter: SYMBOL SHIFT and it; the punctuation the
Spectrum has, typed as on a PC (`"`, `:`, `+`...), as SYMBOL SHIFT and
its key; Backspace: DELETE; the arrows: CAPS SHIFT and 5 to 8. Several
keys at once, held as long as they are held. Page Up pauses, Page Down
turns the sound on and off (off at the start), Escape quits.

**Sound.** The beeper, through the sound service when there is a sound
card (Page Down turns it on); below 45 frames a second for a few seconds
it turns itself off, and Page Down tries again.

**A service.** Each zxspectrum registers `zx<pid>` and serves emu/1: its
registers, memory, a disassembly, the screen as text or as a PNG; pause,
steps, frames, breakpoints and watchpoints; keys typed; tapes and
snapshots loaded, the state saved. The Services window, scripts and the
agent can use it. `zxspectrum --headless [FILE]`: the machine and its
service without a window.

Not emulated: the 128K, memory contention, the floating bus, turbo
loaders (a tape's blocks reach the machine only through the ROM's loader).
