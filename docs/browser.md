# browser

A simple web browser for MyNOS, written in OCaml: it reads HTML and
shows its text, links, pictures and forms, with a little CSS (what
hides, colours, weight, alignment, the layout of lists and menus). No
JavaScript: the pages that do not need it read well (Wikipedia, Hacker
News, the text editions of news sites, documentation, blogs); the others
show what their HTML holds.

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
- CSS, a little of it (`css.ml`): the page's `<style>` blocks and its
  style sheets (`<link rel=stylesheet>`, fetched in parallel after the
  page, which shows at once and takes its style when they come; kept for
  the session), `@media` blocks for the window's width. Selectors: tag,
  `.class`, `#id`, attributes, `*`, `:first-child`, `:last-child`,
  `:not()`, `:link`, and the combinators (descendant, `>`, `+`, `~`); the
  cascade (`!important`, specificity, order, the `style` attribute) and
  `var()` with its fallback. What it does: `display` (`none` hides, a
  block shown inline as menus do, or the other way), `visibility`,
  "visually hidden" elements (`opacity:0`, clipped away, far off),
  `color` (when it reads on white), `font-weight`, `text-decoration`,
  `text-align` (centre, right), `white-space: pre`, `text-transform`,
  `list-style: none`, margins of 1 em or more as a blank line. Not:
  sizes, fonts, boxes, backgrounds, positions, flexbox and grid.
  `BROWSER_TIMES=1 browser --dump URL` says where a page's time went.
- The address field edits at its cursor: a click places it, Left, Right,
  Home, End move it.

Not: JavaScript, layout by CSS boxes, GIF and SVG pictures. Sites that need JavaScript say so:
Google's search, past its cookie notice (whose buttons work), asks for
it; DuckDuckGo's lite version (`lite.duckduckgo.com`) searches without.
