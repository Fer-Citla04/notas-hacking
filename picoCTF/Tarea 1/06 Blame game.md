## **Reto**: Blame game

## **Descripción**
Someone's commits seems to be preventing the program from working. Who is it? You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/72/challenge.zip)

## **Solución**
1. Primero, entré a la carpeta de descargas y luego a donde tenía el `challenge.zip`.
2. Descomprimí el archivo y desde la terminal de kali entré a la carpeta `drop-in`. Al listar los archivos con `ls -la`, vi que había un archivo de Python llamado `message.py` y la carpeta oculta `.git`.
3. Intenté correr el programa con `python3 message.py`, pero me dio un error de sintaxis (`SyntaxError`) porque faltaba cerrar un paréntesis. Esto confirmaba que alguien había hecho modificaciones al código.
4. Después, al querer  ver quién fue el responsable de ese cambio, usé el comando para ver el historial de ese archivo: `git log message.py` y dio como resultado lo siguiente
   `┌──(kali㉿kali)-[~/Downloads/picoCTF/drop-in]`
   `└─$ git log message.py` 
      `commit 9ae3e1bc67ad0143c611c5f65399b79850d20983`
     `Author: picoCTF{@sk_th3_1nt3rn_b64c4705} <ops@picoctf.com>`
     `Date:   Sat Mar 9 21:09:01 2024 +0000`

     `optimize file size of prod code`

     `commit f3cec26cf7f80f91b5c3d1972f14dd4e9f97ec83`
     `Author: picoCTF <ops@picoctf.com>`
     `Date:   Sat Mar 9 21:09:01 2024 +0000`

      `create top secret project`

5. Entonces aparecía el commit más reciente (`9ae3e1b...`) y en la parte donde aparece el Author, en lugar de un nombre  estaba picoCTF
6. Y así fue como encontré la bandera.

```
picoCTF{@sk_th3_1nt3rn_b64c4705}
```

## **Notas adicionales**

- **`git log message.py`**: Este comando me permitió ver quién hizo los cambios en el archivo que no funcionaba. Es muy útil para rastrear errores o, en este caso, encontrar al autor de la flag.
