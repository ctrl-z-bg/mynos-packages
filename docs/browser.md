# browser

A simple web browser for MyNOS, written in OCaml: it reads HTML and
shows its text and its links. No JavaScript and no style sheets: the
pages that do not need them read well (Wikipedia's mobile edition,
Hacker News, the text editions of news sites, documentation, blogs);
the others show what their HTML holds.

```
mynos:/$ pkg install browser
mynos:/$ browser &                       (or the menu's Applications)
mynos:/$ browser en.m.wikipedia.org/wiki/OCaml &
mynos:/$ browser --dump https://text.npr.org/     (the page as text)
```

- Addresses: `http:`, `https:` (MyNOS's TLS), `file:` (a file, or a
  folder of the disk as a list), `about:start`. A typed `example.com`
  is `https://example.com`; `/disk/page.html` is a file.
- Shown: headings, paragraphs, lists, quotes, tables (a row a line, the
  cells separated by `|`), preformatted text, bold, links (blue,
  underlined: a click follows one; the status line shows where it
  goes), images as their `[alt]` text, forms as placeholders.
- Back, Forward, Reload (Stop while a page comes). Page Up, Page Down,
  the arrows, Home and End scroll, when the address field does not have
  the keys. The text can be selected with the mouse and is copied, as in
  every window.
- Redirections are followed; the page's charset is read (UTF-8, or
  Latin-1 and Windows-1252, converted).

Not yet (the next phases): pictures (PNG, JPEG), forms that send,
cookies, a little CSS.
