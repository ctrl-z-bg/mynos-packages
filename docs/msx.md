# msx

An MSX1 or an MSX2 in a window: MyNOS's own emulator, written in OCaml
(MIT), with C-BIOS, a free BIOS (BSD).

```
mynos:/$ pkg install msx
mynos:/$ msx westen                   the game that comes with it (MSX1)
mynos:/$ msx /disk/roms/msx/game.rom  an MSX1
mynos:/$ msx2 /disk/roms/msx/game.rom an MSX2 (or msx --msx2)
```

The MSX1: a Z80 at 3.58 MHz, the TMS9918A (16 KB of VRAM: Graphics I
and II, text, multicolor, 32 sprites), the AY-3-8910 (PSG), 64 KB of
RAM, 60 frames a second.

The MSX2: the same Z80 and PSG, the V9938 (128 KB of VRAM, a palette of
16 colours out of 512, text of 80 columns, SCREEN 4 to 8, sprites of
mode 2 with a colour a line, 212 lines, the vertical scroll, the line
interrupt, the command engine's copies, fills and lines), a memory
mapper of 512 KB, the clock (the host's time); slot 3 expanded, the
SUB-ROM in 3-0 and the RAM in 3-2, as openMSX's C-BIOS MSX2. The
picture is 512 columns wide: the window shows it at once, not doubled.

Both: cartridges of up to 64 KB, and MegaROMs (Konami, Konami SCC
without its sound, ASCII 8 and 16 KB), their kind guessed from their
code. The VDP draws each line as the beam reaches it, so split screens
(a register changed in the middle of a frame) show as they would.

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

A real MSX2's, the same way: its main ROM (32 KB) as
`/disk/roms/msx/msx2.rom` and its SUB-ROM (16 KB, the BASIC's MSX2
part) as `/disk/roms/msx/msx2ext.rom`; both are needed. A machine's
disk ROM, Kanji ROM or MSX-MUSIC are not used.

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

**A service.** Each msx registers `msx<pid>` (msx2: `msx2<pid>`) and
serves emu/1: its
registers, memory (`cpu`, `ram`, `vram`, `rom`; the MSX2's RAM is its
512 KB, its VRAM 128 KB), a disassembly, the screen as text (in the
text modes) or as a PNG; pause, steps, frames,
breakpoints and watchpoints; keys typed; cartridges loaded, states saved
(`.state`, MyNOS's own). `msx --headless [CARTRIDGE]`: the machine and
its service without a window.

Not emulated: the MSX2+ and turbo R, the cassette, disks, the SCC's and
MSX-MUSIC's sound, the key click. Of the V9938: the command engine's
speed (a command is done at once), interlace, the display's adjustment
(register 18), the mouse and the light pen, Graphics 6 and 7's
interleaving of the VRAM (shown only when one mode reads what another
wrote).
