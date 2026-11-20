# MyNOS packages

The packages that [MyNOS](https://github.com/ctrl-z-bg/mynos)'s package
manager, `pkg`, installs: demos and programs, as they are written.

```
mynos:/$ pkg list
mynos:/$ pkg install 2048
mynos:/$ 2048                 (in a Terminal window of the graphical session)
```

This repository holds only what `pkg` downloads, from
`raw.githubusercontent.com`:

```
index.json                    the packages: name, version, description,
                              licence, archive, size, BLAKE2b-256 hash,
                              the MyNOS they were built on
packages/NAME-VERSION.tar     one archive per package and version
```

An archive holds `package.json`, the program as OCaml bytecode, its
sources in `src/`, and its licence. `pkg` checks the archive's size and
hash against the index, then installs the bytecode if this MyNOS can run
it, or compiles the sources inside MyNOS if it cannot.

The packages are described and built in the main repository
(`packages/NAME/spec`, `tools/pkg-build.sh`); this one is its output.
How it works: the MyNOS Reference Manual, 9.8 and appendix H.9, and
`doc/decisions/packages.md`.

## Packages

| Package | What it is | Licence |
|---|---|---|
| `2048` | 2048, the sliding tile game, by Philip Xu ([2048-ml](https://github.com/pyx/2048-ml), 2014), written for OCaml's `Graphics` and unchanged | BSD-3-Clause |
| `windtree` | A tree in the wind: a fractal tree under a night sky, written by MyNOS's agent inside MyNOS (the manual's example of 20.6) | GPL-2.0-or-later |

Each archive carries its own licence, as its `package.json` names it.
