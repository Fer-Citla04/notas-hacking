## **Reto**: 8 -> PW Crack 2

## **Descripción**
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/15/level2.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/15/level2.flag.txt.enc) in the same directory too.

## **Solución**
- Primero se descargan los archivos 
`wget https://artifacts.picoctf.net/c/15/level2.py`
`wget https://artifacts.picoctf.net/c/15/level2.flag.txt.enc`

- Después, se ejecuta el cat en el archivo .py para poder visualizar el código.
`cat level2.py`

- En el código viene lo siguiente: chr(0x33) + chr(0x39) + chr(0x63) + chr(0x65)
  Y lo que se tiene que hacer es hacer la conversión de hexa a código ASCII para poder encontrar la contraseña al momento de ejecutar el .py
- La conversión es 39ce. Ya teniéndola, se ejecuta el archivo .py y cunado pida la contraseña, se introduce.
`python level2.py` 
- Así es como se encuentra la bandera de este reto.
```
picoCTF{tr45h_51ng1ng_502ec42e}
```

## **Notas adicionales**
Se hizo lo mismo que el reto anterior, solo que ahora el código dió la contraseña en hexadecimal.

