# Analizador Sintáctico en Python

Este proyecto implementa un **analizador léxico y sintáctico** sencillo en Python que permite:

1. **Tokenizar** una expresión aritmética de entrada.
2. **Analizar sintácticamente** la expresión usando análisis descendente recursivo.
3. Generar e imprimir el **árbol de sintaxis** correspondiente a la expresión.
4. Guardar el árbol en una imagen (`arbol_sintactico.png`).

## Archivos del proyecto

* **`parser_arbol.py`** - Programa principal integrado que contiene:
  * Un **tokenizador** manual que divide la cadena en tokens (`num`, `id`, operadores, paréntesis).
  * La clase `Parser`, que implementa el análisis sintáctico descendente recursivo.
  * Funciones para **dibujar el árbol de sintaxis** usando `networkx` y `matplotlib`.
  * La ejecución principal que solicita el archivo de entrada y genera el árbol.

* **`arbol_sintactico.png`** - Imagen generada automáticamente con el árbol de sintaxis de la última expresión analizada.
* **`gra.txt`** Aqui encontramos las reglas

## Gramática implementada

El analizador utiliza la siguiente gramática para expresiones aritméticas:

```
E -> E opsuma T | T
T -> T opmul F | F  
F -> id | num | pari E pard
```

Donde:
* `opsuma` = `+` o `-`
* `opmul` = `*` o `/`
* `pari` = `(`
* `pard` = `)`
* `num` = números enteros
* `id` = identificadores (variables)

## Requisitos

Antes de ejecutar, instala las dependencias:

```bash
pip install networkx matplotlib
```

## Ejecución

1. Crea un archivo de entrada (por ejemplo `expresion.txt`) con una expresión aritmética, por ejemplo:
   ```
   8*3+4
   ```

2. Ejecuta el programa:
   ```bash
   python main.py
   ```

3. Ingresa el nombre del archivo cuando lo solicite:
   ```
   Dame el archivo: expresion.txt
   ```

El programa:
* Lee la expresión del archivo.
* Tokeniza la cadena.
* Analiza sintácticamente usando la gramática definida.
* Muestra si fue aceptada por la gramática.
* Genera el árbol de sintaxis en `arbol_sintactico.png`.

## Ejemplos de expresiones válidas

* `8*3+4`
* `x + y * 2`
* `(a + b) * c`
* `123 + var_name`
* `x * (y + z) / w`

## Estructura del árbol generado

El árbol de sintaxis muestra:
* **Nodos internos**: No terminales de la gramática (`E`, `T`, `F`)
* **Hojas**: Terminales (números, identificadores, operadores, paréntesis)
* **Estructura jerárquica**: Precedencia de operadores (multiplicación/división antes que suma/resta)
