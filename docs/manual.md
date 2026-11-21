# manual

The MyNOS Reference Manual, inside MyNOS: its chapters and appendices,
as Markdown, in `/disk/pkg/manual`.

```
mynos:/$ man pkg          a command's entry (chapter 13)
mynos:/$ man Gui          a module's (chapter 24)
mynos:/$ man -k package   the headings that mention a word
mynos:/$ man 9            chapter 9; man E: appendix E
mynos:/$ man -l           the chapters
mynos:/$ manual &         the whole manual in a window, with a search
```

On the console the text goes a screenful at a time: Space or Enter for
more, Q to stop. The package is updated with the manual: `pkg upgrade`
brings the latest.
