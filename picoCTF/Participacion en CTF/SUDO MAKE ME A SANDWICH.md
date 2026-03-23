## **Reto**: SUDO MAKE ME A SANDWICH
## **Descripción**
Can you read the flag? I think you can!`ssh -p 61815 ctf-player@green-hill.picoctf.net` using password `c136b219`
## **Solución**
Al conectarme por SSH y listar los archivos con `ls`, encontré el archivo `flag.txt`. Sin embargo, al intentar leerlo con `cat flag.txt`, el sistema me dio un error de **"Permission denied"**. Esto indica que el archivo solo puede ser leído por el usuario **root**.

Para resolverlo, seguí estos pasos de escalada de privilegios:

1. **Revisar permisos de Sudo:** Ejecuté el comando `sudo -l` para ver qué comandos puedo ejecutar como superusuario sin conocer la contraseña de root.
    
2. **Identificar el vector de ataque:** El resultado mostró que tengo permiso para ejecutar `/usr/bin/emacs` como sudo. Emacs es un editor de texto muy potente que permite ejecutar una terminal (shell) dentro de él.
    
3. **Explotación con Emacs:**
- Ejecuté el editor con privilegios elevados: `sudo emacs`.

- Una vez dentro de la interfaz de Emacs, utilicé el atajo **Alt + X** (o _Meta+X_).

- Escribí el comando `shell` y presioné Enter.

Esto abrió una terminal dentro del editor, pero con los privilegios de quien lanzó el programa (en este caso, **root**). Al ser ahora el usuario con máximo poder, simplemente ejecuté:

`cat flag.txt`

El sistema me mostró la bandera inmediatamente y el reto quedó resuelto.

```
picoCTF{ju57_5ud0_17_f8185e1e}
```
## **Notas adicionales

sudo -l: Es el primer comando que cualquier analista forense o pentester debe ejecutar al ganar acceso a una máquina Linux para encontrar rutas de escalada.

Escalada de Privilegios: Es el proceso de explotar un error, un fallo de diseño o una configuración de permisos para ganar acceso a recursos que normalmente están protegidos.

GTFOBins: Existe una lista famosa llamada GTFOBins que cataloga cómo usar binarios legítimos (como Emacs, Vi o Python) para saltar restricciones de seguridad si tienen permisos de sudo.

