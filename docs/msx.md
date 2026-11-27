# msx

An MSX1 in a window: MyNOS's own emulator, written in OCaml (MIT), with
C-BIOS, a free BIOS (BSD).

```
mynos:/$ pkg install msx
mynos:/$ msx westen                   the game that comes with it
mynos:/$ msx /disk/roms/msx/game.rom
```

The machine: a Z80 at 3.58 MHz, the TMS9918A (16 KB of VRAM: Graphics
I and II, text, multicolor, 32 sprites), the AY-3-8910 (PSG), 64 KB of
RAM, 60 frames a second. Cartridges of up to 64 KB, and MegaROMs
(Konami, Konami SCC without its sound, ASCII 8 and 16 KB), their kind
guessed from their code.

**The game that comes with it** (in `/disk/pkg/msx/games`): `westen`,
Westen House (Santiago Ontañón, 2021-2023, Apache 2.0), an isometric
adventure: the arrows walk, Space and M are a joystick's buttons.

**Other games and ROMs.** C-BIOS starts cartridges only: no MSX-BASIC,
no cassette, no disk. Cartridges (`.rom`, `.mx1`, `.mx2`) of your own:
copy them to `/disk/roms/msx/` (not into `/disk/pkg/msx`, which `pkg`
empties when it updates the package) and give the path. Many free
homebrew games are on https://www.msxdev.org.

A real MSX1's BIOS, proprietary (Microsoft and ASCII's MSX-BASIC), can
take C-BIOS's place if you own one: its main ROM, 32 KB (a dump of
your own machine's; one with the international keyboard matches the
keys here), copied as `/disk/roms/msx/msx1.rom`.
Then `msx` without a cartridge starts MSX-BASIC. Nothing else is
needed: the MSX1 has no other ROM.

**Keys.** Letters, digits and the punctuation as on a PC (the MSX's
international keyboard has the same symbols over the same keys); Enter,
Space, Backspace, Tab, the arrows, Home, Insert, Delete; Ctrl and a
letter: CTRL and it; End: the MSX's ESC. Page Up pauses, Page Down turns
the sound on and off (off at the start), Escape quits. Not reachable
from a window: F1-F5, STOP, SELECT, GRAPH, CODE, and SHIFT or CTRL
alone (emu/1's `keys` has them all).

**Sound.** The PSG's three channels, its noise and envelope, through the
sound service when there is a sound card (Page Down turns it on); below
54 frames a second for a few seconds it turns itself off.

**A service.** Each msx registers `msx<pid>` and serves emu/1: its
registers, memory (`cpu`, `ram`, `vram`, `rom`), a disassembly, the
screen as text (in the text modes) or as a PNG; pause, steps, frames,
breakpoints and watchpoints; keys typed; cartridges loaded, states saved
(`.state`, MyNOS's own). `msx --headless [CARTRIDGE]`: the machine and
its service without a window.

Not emulated: the MSX2 and later, the cassette, disks, the SCC's and
MSX-MUSIC's sound, a change of the VDP's registers in the middle of a
frame (split screens), the key click.
