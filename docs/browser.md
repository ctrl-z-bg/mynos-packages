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

- Pictures: PNG and JPEG (baseline; progressive ones show their words),
  fetched after the page, at their size, narrowed to the page; a picture
  in a link follows it. SVG and GIF show their words.
- Forms: text fields (a click gives them the keys; Enter sends),
  passwords, check boxes, radio buttons, menus (a click shows the next
  choice), buttons; sent by GET or POST. Cookies are kept while the
  window is open, by site.

- Tables: the simple ones (no tables or fields inside: data tables) as
  grids, their columns as wide as their words need, narrowed to fit; the
  others a row a line.
- A little CSS: what the `hidden` attribute, a `display:none` or
  `visibility:hidden` style, or a simple rule of a `<style>` block (a
  tag, `.class`, `#id`) hides is not shown; text colours that read on
  white are kept.

Not: JavaScript, style sheets of their own (`<link rel=stylesheet>`),
layout by CSS, GIF and SVG pictures.
