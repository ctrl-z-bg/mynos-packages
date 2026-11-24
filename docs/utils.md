# utils

Commands for text and files, which MyNOS's `sh` does not have built in.
Each is a program of its own on `/disk/bin`; with no file, each reads its
standard input, so they work in pipes (`ls /disk | sort -r | head -3`).

| Command | What it does |
|---|---|
| `grep [-ivnclrFh] PATTERN [FILE...]` | the lines that match; `-i` without case, `-v` those that do not, `-n` with their numbers, `-c` how many, `-l` the files only, `-r` into directories, `-F` a plain string, `-h` without file names |
| `wc [-lwc] [FILE...]` | lines, words, bytes |
| `head [-n N] [FILE...]`, `tail [-n N\|+N] [FILE...]` | the first or last N lines (10) |
| `sort [-rnfu] [-k N] [FILE...]` | the lines sorted: `-n` as numbers, `-f` without case, `-r` reversed, `-u` once each, `-k` from field N |
| `uniq [-cdui] [FILE]` | a run of equal lines once: `-c` counted, `-d` the repeated, `-u` the others |
| `find [DIR...] [-name P] [-iname P] [-type f\|d] [-maxdepth N]` | the files under DIR whose name matches the pattern |
| `du [-shb] [PATH...]` | space used, in KB: `-s` the total, `-h` in K/M/G, `-b` in bytes |
| `df [-h]` | the file systems (`/` the RAM disk, `/tmp`, `/disk`): size, used, free, each service asked through its protocol |
| `hexdump [-n N] [-s OFFSET] [FILE...]` | bytes in hexadecimal and as text |
| `clip [TEXT...]` | the clipboard (the system's, shared with the windows): prints it; with words, or from a pipe (`ls \| clip`), copies |
| `tree [-ad] [-L N] [DIR...]` | directories as a tree |
| `top [-b] [-n N] [-d SECS]` | the processes, the busiest first: CPU %, memory, threads, page faults a second, and the processor's load and the memory in use; again every SECS seconds (1) until `q`, or `-b` N tables (1) one after the other |

`grep`'s patterns are OCaml's `Str` regular expressions, written as in
Emacs: `.` `*` `+` `?` `[...]` `^` `$`, `\|` between alternatives,
`\(` `\)` around a group. Quote them, so that `sh` leaves them alone:
`grep -n 'let \(rec \)?go' /disk/src/*.ml`. Patterns for `find` are the
shell's (`*`, `?`, `[...]`), quoted too: `find /disk -name '*.ml'`.

Exit status: 0, or 1 when a file could not be read; `grep` 0 when a line
matched, 1 when none did, 2 on an error.
