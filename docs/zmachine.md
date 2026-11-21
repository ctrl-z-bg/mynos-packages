# zmachine

An interpreter of the Z-machine, the virtual machine of Infocom's
interactive fiction (1979 to 1989) and of the games written since with
Inform. It plays story files of versions 1 to 5, 7 and 8 (`.z3`, `.z5`,
`.z8`); not version 6, with pictures.

```
mynos:/$ pkg install zork1        (zmachine comes with it)
mynos:/$ zork1                    (or: zmachine zork1)
mynos:/$ zmachine /disk/games/curses.z5
mynos:/$ zmachine -t zork1        (in the terminal, in the graphical session too)
```

In the graphical session the story plays in a window: the status line
(or the game's upper window) on top, the text below it, kept as it goes
(the wheel, Page Up and Page Down scroll back); Up and Down recall what
you typed. Started from the Packages window or the menu without a
story, it asks for one. Outside the graphical session, or with `-t`, it
plays in the terminal.

`save` and `restore` ask for a file name; Enter takes the default,
`/disk/STORY.sav`. `undo` works in the games that offer it (version 5
and later).

Infocom's Zork I, II and III, under the MIT licence since 2025, are
packages: `zork1`, `zork2`, `zork3`. Free stories are on the IF Archive
(https://www.ifarchive.org/indexes/if-archive/games/zcode/): copy one to
`/disk` and give its name to `zmachine`.
