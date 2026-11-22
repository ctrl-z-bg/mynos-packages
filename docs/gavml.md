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
ends a game.

The game runs in steps of 20 ms (GAV's 50 a second), whatever the
window's pace; its sounds are short tones, through MyNOS's sound
service when there is one.

Not yet: the network game of the original (a later version).
