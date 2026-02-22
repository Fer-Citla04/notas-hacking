## **Reto**: Commitment issue

## **Descripción**
I accidentally wrote the flag down. Good thing I deleted it! You download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/139/challenge.zip)

## **Solución**
1. Primero, entré a mi carpeta de descargas y descomprimí el archivo `challenge.zip`.

2. Al listar los archivos con `ls -la`, vi que había una carpeta llamada `drop-in` y otra llamada `Addadshashanammu`, pero la importante resultó ser `drop-in` porque contenía una carpeta oculta `.git`.

3. Entré a la carpeta `drop-in` y usé el comando `git log` para ver el historial de cambios del proyecto.

4. En el historial aparecieron dos momentos: uno donde decían que habían borrado información sensible (`remove sensitive info`) y otro anterior donde se creó la bandera (`create flag`).

5. Copié el código (hash) del momento donde se creó la bandera: `7d3aa557ff7ba7d116badaf5307761efb3622249`.

6. Usé el comando `git checkout 7d3aa557ff7ba7d116badaf5307761efb3622249` para regresar los archivos a ese estado anterior.

7. Al hacer `ls -la` de nuevo, vi que el archivo `message.txt` ahora pesaba más, lo que indicaba que ya no estaba vacío.

8. Finalmente, leí el archivo con `cat message.txt` y encontré la bandera.

```
picoCTF{s@n1t1z3_be3dd3da}
```

## **Notas adicionales**

- **`git log`**: Es el comando que te permite ver el pasado del proyecto. Sin esto no habríamos sabido que la bandera existió antes de ser borrada.

- **El Hash (`7d3aa5...`)**: Es el identificador único de cada cambio. Es como una dirección que le dice a Git exactamente a qué punto del tiempo queremos volver.

- **`git checkout`**: Este comando es el que hace la magia de restaurar los archivos eliminados basándose en el historial del repositorio.

- **`.git`**: Es la carpeta donde se guarda toda la "memoria" del reto. Si no existe esa carpeta, no se podrían usar estos comandos.

