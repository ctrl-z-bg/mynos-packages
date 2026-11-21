# wiki

Wikipedia, in a window or in the terminal, through its API (JSON over
HTTPS).

In the window: type a subject and press Enter; the small field on the
left is Wikipedia's language (`en`, `it`, `de`, `fr`...). A result opens
its article; **Links** lists the articles it links to, each one a click
away; `<` goes back; **Random** opens any article.

In the terminal:

```
mynos:/$ wiki Microkernel             the article's first paragraphs
mynos:/$ wiki -l it Pantelleria       in Italian
mynos:/$ wiki -f OCaml                the whole article
```

It also gives MyNOS's agent a tool, `wikipedia`: asked about a fact, the
agent can look it up.
