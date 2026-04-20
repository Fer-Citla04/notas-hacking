## **Reto**:  The numbers
## **Descripción**
The numbers... what do they mean?[numbers.png](https://challenge-files.picoctf.net/c_fickle_tempest/7b39deba4212c233b1628c93f16639ed02ad90f51436d2a8914bb11f74a982d3/the_numbers.png)
## **Solución**
1. Primero, descargué la imagen. Al abrirla, noté que los números estaban organizados como la estructura PICOCTF{...}. 
2. Al observar los valores, identifiqué que todos se encontraban en un rango del 1 al 26.
3. Para resolver esto de manera eficiente y profesional, utilicé un script de Python diseñado para procesar una lista mixta de enteros y caracteres especiales.
d`ef convert_to_text(numbers):`
    `letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"`
    `result = ""`
    `for item in numbers:`
        `if isinstance(item, int):`
            `result += letters[item - 1]`
        `else:`
            `result += str(item)`
    `return result`

`list_to_convert = [16, 9, 3, 15, 3, 20, 6, "{", 20, 8, 5, 14, 21, 13, 2, 5, 18, 19, 13, 1, 19, 15, 14, "}"]`
`print(convert_to_text(list_to_convert))`

4.  La bandera obtenida fue la siguiente
```
PICOCTF{THENUMBERSMASON}
```

## **Referencias
https://medium.com/@sobatistacyber/picoctf-writeup-the-numbers-845b15226a19