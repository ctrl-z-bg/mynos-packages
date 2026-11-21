# calc

A calculator of exact numbers, on OCaml's `Num` library: integers have
no limit, fractions stay fractions, and decimals can be as long as you
ask.

```
mynos:/$ calc
> 2^100
1267650600228229401496703205376
> 1/3 + 1/6
1/2 = 0.5
> 0.1 + 0.2
3/10 = 0.3
> factor(2^32 + 1)
641 * 6700417
> digits 50
> 1/7
1/7 ~ 0.14285714285714285714285714285714285714285714285714
> sqrt(2)
~1.4142135623731
> quit
mynos:/$ calc '30!' 'C(52, 5)'
265252859812191058636308480000000
2598960
```

- **Numbers**: `123`, `1_000_000`, `0.25` (exact: 1/4).
- **Operators**: `+ - * / %`, `^` or `**`, `!` (factorial), brackets.
  `^` groups from the right and binds tighter than a minus: `-3^2` is -9.
- **Functions**: `sqrt` (exact for squares), `abs floor ceil round`,
  `num den` (of a fraction), `gcd(a, b) lcm(a, b)`, `C(n, k)`, `fib(n)`,
  `isprime(n)`, `factor(n)` (by trial division: numbers of a calculator,
  not of cryptography).
- **Approximations**, marked `~`: `sqrt` of a non-square, `sin cos tan
  asin acos atan`, `ln log exp`, `pi e`.
- **Names**: `x = 2^10` keeps a value; `_` is the last result; `vars`
  lists them.
- `digits N` sets the decimals shown (20); `help`; `quit` or Ctrl-D.

With expressions as arguments, `calc` prints each result and ends (exit
status 1 if one failed): `calc '2^64 - 1'`. Quote them: `sh` reads `*`
and `!` otherwise.
