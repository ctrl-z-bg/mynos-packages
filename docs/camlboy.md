# camlboy

A Game Boy, in a window: CAMLBOY, the emulator written in OCaml by
linoscope (MIT licence), with a window of MyNOS's.

```
mynos:/$ pkg install camlboy
mynos:/$ camlboy tobutobugirl         the game that comes with it
mynos:/$ camlboy /disk/roms/gb/game.gb
```

Arrows: the cross; X: A; Z: B; Enter: Start; Space: Select; P pauses;
M turns the sound off and on; Escape quits.

**Sound.** The Game Boy's four channels (two squares, the wave, the
noise) are emulated by MyNOS's `apu.ml` and played through the sound
service, when there is a sound card (`run-demo.sh` gives one). Below 50
frames a second for a few seconds the sound would stutter, so it turns
itself off (the status line says "no sound (slow)").

It needs a fast machine: the Game Boy's 60 frames a second, it reaches
under QEMU with KVM (`run-demo.sh` uses it when it can) or on a PC;
QEMU without KVM gives about a third. A button is down exactly while its
key is held, several at once: Right held and X, and the jump goes on
running.

**The game that comes with it** (in `/disk/pkg/camlboy/games`):
`tobutobugirl`, Tobu Tobu Girl (Tangram Games, 2017; its code MIT, its
art and music CC BY 4.0), an arcade platformer.

**Other games and ROMs.** No boot ROM is needed (the machine starts
where Nintendo's would leave it). Cartridges (`.gb`) of your own: copy
them to `/disk/roms/gb/` (not into `/disk/pkg/camlboy`, which `pkg`
empties when it updates the package) and give the path. The cartridges
it knows: no mapper, MBC1, MBC2, MBC3 (without its clock); not MBC5, nor
the Game Boy Color's. Many free homebrew games are on
https://hh.gbdev.io.

**A service.** Each camlboy registers `camlboy<pid>` and serves emu/1, as
`zxspectrum` does: the CPU's registers, memory (cpu, rom, vram, ram), a
screenshot; pause, steps, frames, breakpoints on the PC; buttons pressed
(`A B START SELECT UP DOWN LEFT RIGHT`). Not here yet: a disassembler,
watchpoints, saved states; a Game Boy has no text screen. `camlboy
--headless ROM.gb`: the machine and its service without a window.
