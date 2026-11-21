# scheme

OCS, a Scheme (R5RS) written in OCaml by Ville-Pertti Keinonen
(2003-2004, BSD licence), changed for OCaml 5 and MyNOS
(`third_party/ocs/MYNOS.md` in MyNOS's sources).

```
mynos:/$ scheme
> (define (fact n) (if (= n 0) 1 (* n (fact (- n 1)))))
> (fact 30)
265252859812191058636308480000000
> (exit)
mynos:/$ scheme /disk/prog.scm         (a file, run)
```

Numbers are exact where Scheme wants them (integers without limit,
fractions: `(/ 1 3)`), through OCaml's Num. `call-with-current-continuation`,
`dynamic-wind`, `define-syntax` with `syntax-rules`, ports on files
(`open-input-file`, `with-output-to-file`...), `load`. `(exit)` or Ctrl-D
ends.
