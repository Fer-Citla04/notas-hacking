## **Reto**: Collaborative development

## **Descripción**
My team has been working very hard on new features for our flag printing program! I wonder how they'll work together? You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/178/challenge.zip)

## **Solución**
1. Primero, descargamos el zip y lo descomprimimos.
2. Al entrar a la carpeta `drop-in` y usar `ls -la`, vi el archivo `flag.py` y la carpeta de `.git`.
3. Intenté leer el archivo con `cat flag.py`, pero solo decía "Printing the flag.", así que supe que la bandera no estaba en la rama principal.
4. Después usé el comando `git branch -a` para ver si había más ramas y sí aparecieron: `feature/part-1`, `feature/part-2` y `feature/part-3`.
5. Luego lo que hice fue que fui saltando de rama en rama para juntar las partes, ya que la bandera iba a venir por partes:
   - En `feature/part-1` saqué: `picoCTF{t3@mw0rk_`
   - En `feature/part-2` saqué: `m@k3s_th3_dr3@m_`
   - En `feature/part-3` saqué: `w0rk_6c06cec1}`

6. Al final, junté las tres partes y así encontré la bandera completa de este reto.
   
```
picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_6c06cec1}
```
## **Notas adicionales**
Otra forma para resolverlo es poner el comando `git diff feature/part-1 && git diff feature/part-2 && git diff feature/part/3`

- **`git log`**: se usa para ver el historial, aunque en este caso solo te mostró el commit inicial de la rama principal.
- **`git branch -a`**: Es el comando que te enlistó todas las ramas disponibles.
- **`git checkout`**: Es el comando para cambiar de "contexto" o rama. Al usarlo, Git cambia los archivos de tu carpeta por los que pertenecen a esa rama específica.
- **`git diff`**: Este comando se usa para ver las diferencias entre las ramas. Mostró qué líneas de código se quitaron (`-`) y cuáles se pusieron (`+`) entre una versión y otra.

