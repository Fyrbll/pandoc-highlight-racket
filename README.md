# Racket Syntax Highlighting for Pandoc-Flavored Markdown

## Usage

Suppose you have a Pandoc-flavored markdown file with Racket code blocks of the
form

    ```racket
    (define (f x) (abs (- x 10)))
    ```

Add `--syntax-definition=`_PATH TO racket.xml_ to your usual invocation of
Pandoc in the command line and the generated HTML or LaTeX will have
syntax-colored Racket code.

### Example

Consider the Pandoc-flavored markdown file **example.md** included in the
this repository's **example** folder.

I would normally run the following to generate a standalone HTML from
example.md though it wouldn't color Racket blocks.

        $ pandoc \
        > --standalone \
        > --metadata title="Example" \
        > --output=example-no_rkt_hl.html \
        > example.md

Now that I have a Racket syntax definition namely **racket.xml** available I can
instruct Pandoc to use it to highlight Racket code.

        $ pandoc \
        > --syntax-definition=../racket.xml \
        > --standalone \
        > --metadata title="Example" \
        > --output=example-rkt_hl.html \
        > example.md

I can add yet another command line argument to apply the alternative **kate**
highlighting style that comes installed with Pandoc.

        $ pandoc \
        > --syntax-definition=../racket.xml \
        > --highlight-style=kate \
        > --standalone \
        > --metadata title="Example" \
        > --output=example-rkt_hl_kate.html \
        > example.md

I have included the files **example-no_rkt_hl.html**, **example-rkt_hi.html**
and **example-rkt_hl_kate.html** as generated on my computer running pandoc 2.13
on macOS 11.1 in the **examples** folder.

## Nuances

The highlighter assumes your Racket or Typed Racket code is _free of syntax
errors_, in other words the code ought to be accepted by the Racket interpreter.

The highligher _does not support_ S-expression comments, the nesting of block
comments, `#! ` comments or `#!\` comments. Single line comments i.e. `;` and block
comments with one level of nesting e.g. `#| a #| comment |#` are okay.

## Contributing

Please feel free to use the Issues tab to post questions and comments about the
implementation of **racket.xml** and to suggest improvements.

Pull requests are welcome!

## References

The [Pandoc User's Guide](https://pandoc.org/MANUAL.html) for information on how
to supply Pandoc with a new syntax definition file.

Emacs' [racket-mode](https://github.com/greghendershott/racket-mode) for the
list of keywords as well as the strategy for highlighting `#lang`, `module`,
`define` and `define-values` forms.

[Working with Syntax
Highlighting](https://docs.kde.org/trunk5/en/kate/katepart/highlight.html) from
[The KatePart Handbook](https://docs.kde.org/trunk5/en/kate/katepart/index.html)
for instructions on writing a syntax definition from scratch.

The [KDE-style XML syntax definition for
Scheme](https://github.com/KDE/syntax-highlighting/blob/master/data/syntax/scheme.xml)