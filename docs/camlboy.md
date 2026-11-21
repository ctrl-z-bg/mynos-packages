# camlboy

A Game Boy, in a window: CAMLBOY, the emulator written in OCaml by
linoscope (MIT licence), with a window of MyNOS's.

```
mynos:/$ pkg install tobutobugirl     (camlboy comes with it)
mynos:/$ tobutobugirl                 (or: camlboy /disk/games/game.gb)
```

Arrows: the cross; X: A; Z: B; Enter: Start; Space: Select; P pauses;
Escape quits.

It needs a fast machine: the Game Boy's 60 frames a second, it reaches
under QEMU with KVM (`run-demo.sh` uses it when it can) or on a PC;
QEMU without KVM gives about a third. A button is down exactly while its
key is held, several at once: Right held and X, and the jump goes on
running.

Games: `tobutobugirl` (Tangram Games, MIT and CC BY 4.0). Many other
free Game Boy games (homebrew) can be copied to `/disk` and played the
same way.
