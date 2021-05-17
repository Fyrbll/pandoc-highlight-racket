```racket
(module safe-vector-ops typed/racket #:with-refinements

; this is a line comment

#| this is the first line of a block comment,
   and this is its second line
|#

  (module+ main
    (display "display is a keyword,\
\and this is a string"))

  (define-values (truth falsity) (values #t #f))

  (: a-symbol Symbol)
  (define a-symbol '|not a cymbal|)

  (define a-regexp #rx"finding a match")

  (define a-bytestring #"have a byte")

  (define some-numbers '(-1       1/2        1.0   1+2i
                         1/2+3/4i 1.0+3.0e7i 2e5   #i5
                         #e2e5    #x2e5      #b101 +inf.0))

  (define seven (let ([x -7]) (abs x)))

  (: some-characters (Listof Char))
  (define some-characters '(#\space #\u3bb))

  (: curried-int-add (-> Integer (-> Integer Integer)))
  (define ((curried-int-add x) y) (+ x y)))
```