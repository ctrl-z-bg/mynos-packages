# MyNOS packages

The packages that [MyNOS](https://github.com/ctrl-z-bg/mynos)'s package
manager, `pkg`, installs: demos and programs, as they are written.

```
mynos:/$ pkg list
mynos:/$ pkg install 2048
mynos:/$ 2048                 (in a Terminal window of the graphical session)
```

This repository holds only what `pkg` downloads, from
`raw.githubusercontent.com`, and the packages' documentation:

```
index.json                    the packages: name, version, description,
                              licence, archive, size, BLAKE2b-256 hash,
                              the MyNOS they were built on, the packages
                              they need, their commands
packages/NAME-VERSION-HASH.tar  one archive per package and build (HASH: the
                              start of its BLAKE2b-256; the previous index's
                              archives stay, for caches that still serve it)
docs/NAME.md                  a package's documentation
```

An archive holds `package.json`, the program as OCaml bytecode, its
sources in `src/`, its licence and its documentation. `pkg` checks the
archive's size and hash against the index, installs first the packages
it needs, then installs the bytecode if this MyNOS can run it, or
compiles the sources inside MyNOS if it cannot. A package of data (a
story, a game) has no program: the package it needs plays it.

The packages are described and built in the main repository
(`packages/NAME/spec`, `tools/pkg-build.sh`); this one is its output.
How it works: the MyNOS Reference Manual, 9.8 and appendix H.9, and
`doc/decisions/packages.md`.

## Packages

**Commands, for the terminal**

| Package | What it is | Licence |
|---|---|---|
| [`utils`](docs/utils.md) | `grep`, `wc`, `head`, `tail`, `sort`, `uniq`, `find`, `du`, `df`, `hexdump`, `tree`, `clip` | GPL-2.0-or-later |
| [`calc`](docs/calc.md) | a calculator of exact numbers: integers without limit, fractions, factors | GPL-2.0-or-later |
| [`manual`](docs/manual.md) | the MyNOS Reference Manual inside MyNOS: `man pkg`, `man Gui`, and a window to read it | GPL-2.0-or-later |
| [`scheme`](docs/scheme.md) | Scheme (R5RS): OCS by Ville-Pertti Keinonen, changed for OCaml 5 | BSD-2-Clause |

**Windows, for the graphical session**

| Package | What it is | Licence |
|---|---|---|
| [`wiki`](docs/wiki.md) | Wikipedia: search, read, follow the links (and `wiki TERM` in the terminal) | GPL-2.0-or-later |
| [`feeds`](docs/feeds.md) | a reader of news feeds, RSS and Atom | GPL-2.0-or-later |
| [`view`](docs/view.md) | an image viewer: PNG, BMP, PPM, PGM, PBM | GPL-2.0-or-later |
| [`paint`](docs/paint.md) | drawing with the mouse, saved as PNG | GPL-2.0-or-later |
| [`life`](docs/life.md) | Conway's Game of Life, with famous patterns and RLE files | GPL-2.0-or-later |
| `windtree` | a tree in the wind, written by MyNOS's agent inside MyNOS (the manual's 20.6) | GPL-2.0-or-later |
| [`studio`](docs/studio/) | MyNOS Studio: an IDE for OCaml inside MyNOS; build and run, completion from the running services, Watch under the event recorder, services of your own, an agent that edits through Studio's own protocol | GPL-2.0-or-later |
| [`browser`](docs/browser.md) | a simple web browser: text, links, pictures (PNG, JPEG), forms, cookies, tables, CSS style sheets; http and https, no JavaScript; `browser --dump URL` | GPL-2.0-or-later |
| [`sysmonitor`](docs/sysmonitor.md) | the system at work: CPU and memory with their graphs, the disks, the processes (CPU, memory, threads, page faults), ending one; needs a MyNOS of 2026-11-23 or later | GPL-2.0-or-later |

**Games**

| Package | What it is | Licence |
|---|---|---|
| [`mines`](docs/mines.md) | mines, at three levels | GPL-2.0-or-later |
| [`blocks`](docs/blocks.md) | falling blocks | GPL-2.0-or-later |
| [`snake`](docs/snake.md) | the snake that grows | GPL-2.0-or-later |
| [`sudoku`](docs/sudoku.md) | sudoku, made on the spot, with hints | GPL-2.0-or-later |
| [`solitaire`](docs/solitaire.md) | Klondike patience | GPL-2.0-or-later |
| [`gavml`](docs/gavml.md) | GavML: GAV, GPL Arcade Volleyball ([gav](https://github.com/ctrl-z-bg/gav), 2002-), ported to OCaml for MyNOS: 1 or 2 players a side, keyboard, computer or network (with GAV too) | GPL-2.0-or-later |
| `2048` | 2048, by Philip Xu ([2048-ml](https://github.com/pyx/2048-ml), 2014), unchanged | BSD-3-Clause |
| [`minotaur`](docs/minotaur.md) | a text adventure inside MyNOS: you are a message, the Minotaur keeps the ports | GPL-2.0-or-later |
| [`zmachine`](docs/zmachine.md) | a Z-machine interpreter: Infocom's and Inform's interactive fiction | GPL-2.0-or-later |
| [`camlboy`](docs/camlboy.md) | a Game Boy: CAMLBOY, by linoscope, in a window of MyNOS's | MIT |
| `tobutobugirl` | Tobu Tobu Girl (Tangram Games, 2017), for the Game Boy; needs `camlboy` | MIT, CC BY 4.0 |
| `zork1` | Zork I: The Great Underground Empire (Infocom, 1980); needs `zmachine` | MIT |
| `zork2` | Zork II: The Wizard of Frobozz (Infocom, 1981); needs `zmachine` | MIT |
| `zork3` | Zork III: The Dungeon Master (Infocom, 1982); needs `zmachine` | MIT |

Each archive carries its own licence, as its `package.json` names it.
The Zork story files are those Microsoft published under the MIT
licence in 2025 ([historicalsource/zork1](https://github.com/historicalsource/zork1),
[zork2](https://github.com/historicalsource/zork2),
[zork3](https://github.com/historicalsource/zork3)), unchanged; the
games' names are trademarks, which the licence does not cover.
Two packages give MyNOS's agent a tool: `wiki` (`wikipedia`) and `calc`
(`calculate`).
