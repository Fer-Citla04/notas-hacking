## **Reto**: Time machine

## **Descripción**
What was I last working on? I remember writing a note to help me remember... You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/67/challenge.zip)

## **Solución**
1. Primero descargué el ZIP .
2. Al entrar a la carpeta `drop-in` está un archivo de texto message. Entrando al .txt estaba el siguiente mensaje `This is what I was working on, but I'd need to look at my commit history to know why...`
   lo que es una pista.
3. En la misma carpeta drop-in, está otra carpeta llamada `.git` por lo que entramos a ella.
4. Dentro de .git observamos que están varios archivos, incluyendo un .txt que se llama `COMMIT_EDITMSG`.
5. Al abrir el .txt nos da la bandera de este reto.

```
picoCTF{t1m3m@ch1n3_5cde9075}
```


## **Notas adicionales**
Otra forma de resolverlo es desde la terminal.
Cuando estemos en la carpeta drop-in poner el comando `git log --all --oneline`

Cuando se guardan cambios en Git, el sistema obliga a poner una descripción de lo que se hizo usando el comando `git commit -m "mensaje"`.
Lo que pasó es que el programador usó la bandera como descripción: `git commit -m "picoCTF{t1m3m@ch1n3_5cde9075}"`

- **`git log --all --oneline`**: Este comando es como pedirle a Git un resumen de todo lo que ha pasado.
- **`git log`**: Muestra el historial de cambios
- **`--all`**: Le dice a Git que busque en todas las ramas y rincones del historial, no solo en donde estamos.
- **`--oneline`**: Comprime toda la información de cada cambio (autor, fecha, mensaje) en una sola línea para que sea más fácil de leer.
