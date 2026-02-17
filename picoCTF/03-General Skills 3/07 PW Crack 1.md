## **Reto**: 7 -> PW Crack 1

## **Descripción**
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/10/level1.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/10/level1.flag.txt.enc) in the same directory too.

## **Solución**
- Primero, se descargan ambos archivos 
`wget https://artifacts.picoctf.net/c/29/password_checker.py` `wget https://artifacts.picoctf.net/c/29/level1.flag.txt.enc`

- Se ejecuta el cat para visualizar el código y poder sacar el password que se piedo al ejecutar el .py.
`cat level1.py`
- Luego, se abre el archivo del script con el editor de texto para investigar cómo verifica la contraseña se ejecuta el archivo .py
`python level1.py`
- Cuando el programa pida la contraseña, se ingresa la palabra que se encontro dentro del código y se presiona **Enter**. En mi caso fue `691d`
- Así es como se consigue la bandera: 
```
picoCTF{545h_r1ng1ng_56891419}
```

## **Notas adicionales**
- cat: para visualizar el archivo.


