## **Reto**:  MatchTheRegex
## **Descripción**
How about trying to match a regular expression The website is running [here](http://saturn.picoctf.net:64109/).

## **Solución**
1. Lo primero que se hizo fue acceder a la página del reto y abrir el código fuente.
2. Después, se localizó en la parte inferior del documento HTML un bloque de código en JavaScript que se encarga de realizar la validación cuando se presiona el botón "submit".
3. Al revisarlo, se extrajo el patrón que el sistema intenta validar, el cual era: `^p.....f!?`.
4. Con ayuda de RegExr se concluyó que el símbolo `^p` indica que debe iniciar con "p", los cinco puntos `.....` representan cinco caracteres, la f indica el final y el `!?` un signo de exclamación.
5. Luego, se ingresó en el campo de texto una palabra que cumpliera estas condiciones, en este caso fue p12345F.
6. Esta misma palabra, se puso para poder ingresar y al dar submit se apareció la bandera del reto.

```
picoCTF{succ3ssfully_matchtheregex_0694f25b}
```

Otra forma de resolver el reto es mediante Python:

`import re`

`regex_pattern = r"^p.....f!?"`

`test_input = "picoctf"`

`if re.match(regex_pattern, test_input):`
    `print(f"La cadena '{test_input}' es válida.")`
`else:`
    `print("La cadena no coincide con el patrón.")`

## **Referencias
https://www.youtube.com/watch?v=YZemkSTN50U&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=64