# GavML

GAV, GPL Arcade Volleyball, a remake of the DOS game Arcade Volleyball,
written in C++ and SDL from 2002 (https://github.com/ctrl-z-bg/gav),
ported to OCaml for MyNOS (hence its name): the same physics, the same computer players,
the "classic" pictures.

```
mynos:/$ pkg install gavml
mynos:/$ gavml &                 (or the menu's Applications)
```

Choose who plays each of the four places (Left 1 and Right 1 always
play; Left 2 and Right 2 may be nobody): the keyboard or the computer.
So: one against the computer, one against one, two against two, or you
and the computer against two others.

| Place | Left | Right | Jump |
|---|---|---|---|
| Left 1 | z | c | x |
| Right 1 | Left arrow | Right arrow | Up arrow |
| Left 2 | h | k | u |
| Right 2 | s | f | e |

The rules are the original's: only the side that serves scores a point;
a side may touch the ball three times; 15 points win, by two. Escape
ends a game; M turns the sounds off and on (the players' choice has a
button too).

The game runs in steps of 20 ms (GAV's 50 a second), whatever the
window's pace; its sounds are short tones, through MyNOS's sound
service when there is one.


`GAVML_DEBUG=1 gavml &` writes to MyNOS's log (the Log window, or `log`)
once a second: the ball, the score, the frames drawn in that second and
the milliseconds spent stepping the game and drawing it.

## Over the network, with GavML or GAV

A place can be **network**: a player on another machine, running GavML
or GAV for Linux (its network game speaks the same UDP protocol, port
7145). Choose the places and Play: GavML waits for the network's players,
then plays, sending them what happens at every frame and taking their
keys. On the other machine: **Join a game**, the server's address, a
side; its keys are z c x or the arrows.

Under QEMU, MyNOS is behind the host: to be a server it needs the port
forwarded, `UDP=7145 tools/run-demo.sh` or `run-mynos.sh --udp 7145`, and
the others join the host's address. Two MyNOS on the same computer: one
started so, the other joins 10.0.2.2 (the host, as QEMU's network shows
it).

