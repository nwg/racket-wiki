## Split a string into lines (skipping empty lines)
|[[Artifacts]]|
```racket
(regexp-split "\n+" str)
(string-split str #rx"\n+")  ;; string-split also accepts regular expressions
```
`#rx"..."` and `#px"..."` are literal notations for regular expressions [Reading Regular Expressions](https://docs.racket-lang.org/reference/reader.html?q=px#%28idx._%28gentag._87._%28lib._scribblings%2Freference%2Freference..scrbl%29%29%29)

## Split a string into lines (keeping empty lines)
```racket
(string-split str "\n")
```