# zxspectrum

A ZX Spectrum 48K, in a window: MyNOS's own emulator, written in OCaml
(MIT), with the Spectrum's ROM (Amstrad's permission: ROM-LICENSE).

```
mynos:/$ pkg install glazx            (zxspectrum comes with it)
mynos:/$ glazx                        (or: zxspectrum /disk/games/game.tap)
```

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
