## **Reto**: 9 -> PW Crack 3

## **Descripción**
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/18/level3.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/18/level3.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/18/level3.hash.bin) in the same directory too.There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script.

## **Solución**
- Se descargan los archivos
wget https://artifacts.picoctf.net/c/18/level3.hash.bin
wget https://artifacts.picoctf.net/c/18/level3.flag.txt.enc
wget https://artifacts.picoctf.net/c/18/level3.py

- Luego se ejecuta el archivo .py para visualizar el código y en él vienen varias contraseñas.
.#The strings below are 7 possibilities for the correct password. 
#(Only 1 is correct)
pos_pw_list = ["8799", "d3ab", "1ea2", "acaf", "2295", "a9de", "6f3d"]
- Una de la forma de encontrar la bandera es poner la contraseña una por una hasta encontrar la correcta.
- En mi caso, la correcta es `2295` .
- La bandera en este reto es
```
picoCTF{m45h_fl1ng1ng_6f98a49f}
```

## **Notas adicionales**

## **Referencias**
