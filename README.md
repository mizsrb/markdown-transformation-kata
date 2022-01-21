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

## Outside-in steps and ideas

- Interpretar linea de comandos
- Leer un fichero markdown y comprobar que es valido sintacticamente
- Escribir un fichero markdown
- Transformar lineas de markdown
      - Se puede abordar linea a linea? o un enlace puede estar en varias lineas?
      - Las notas pueden estar todas al final del fichero?
      - Reglas de transformacion
- Devuelva: ...???

Artefacto que lee la linea de terminal.
Artefacto que lee un flujo de lineas de un fichero - Quality attributes / Arquitectura / Requisitos no funcionales

      Requisitos no funcionales:
            - Encoding, que encoding?
            - Tamaño de los ficheros
            - Si el idioma repercuta en algo.
            - Tiempo de respuesta, ¿es importante?
            - Que cosas hay en el docker? Que limitaciones tengo? Nos tenemos que ceñir a algun stack?
            - Los archivos son locales? o vienen de red?
            - Inicialmente es un fichero local en disco.
            - Que pasa si el disco duro esta lleno?
            - Batch processing


 Transformar / Reglas de transformacion:  - TODO list:

Happy path todo en una linea: ver doc

Input:
[this book](https://codigosostenible.com) and some other text.
Output:
this book [^anchor1] and some other text.

[^anchor1]: https://codigosostenible.com

Happy path con varios enlaces:

Input:
[this book](https://codigosostenible.com) and some other text [and another link](http://url.com)
Output:
this book [^anchor1] and some other text and some other text and another link [^anchor2]

[^anchor1]: https://codigosostenible.com
[^anchor2]: https://url.com

Casos limite:

Enlaces duplicados:

Input:

[this book](https://codigosostenible.com) and some other text [and another link](https://codigosostenible.com)

Output:

this book [^anchor1] and some other text and some other text and another link [^anchor1]

[^anchor1]: https://codigosostenible.com
