# Markdown transformation kata

The goal is to implement a command line tool that takes a markdown file and returns another markdown file, applying certain transformations to the text. 

The first transformation is to turn links into footnotes. The syntax of a link is this:

```
[visible text link](url)
```

The syntax of a footnote is the following:

```
visible text [^word]

[^word]: url or text 
```

The goal is to make conversions like the following:

Source:

```
[this book](https://codigosostenible.com) and some other text
and some other text line.
```

Transformation:

```
this book [^book1] and some other text 
and some other text line.

[^book1]: https://codigosostenible.com
```




