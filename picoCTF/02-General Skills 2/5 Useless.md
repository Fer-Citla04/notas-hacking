## **Reto**: 5 -> Useless

## **Descripción**
There's an interesting script in the user's home directory

Additional details will be available after launching your challenge instance.
## **Solución**
- Lo primero que hice fue establecer la conexión con el servidor del reto. Después de un par de intentos fallidos, me aseguré de especificar el usuario correcto (**picoplayer**) y el puerto asignado (**49555**) usando el siguiente comando:

**ssh picoplayer@saturn.picoctf.net -p 49555**

Al introducir la contraseña **password**, logré entrar al sistema.

- Una vez dentro, encontré un archivo llamado **useless**. Para entender qué hacía, utilicé el comando de lectura para ver su contenido:

**cat useless**

El script resultó ser una calculadora básica, pero el código tenía un mensaje muy claro: si no funcionaba, debía consultar el manual del programa.

- Siguiendo la pista del propio script, decidí usar la herramienta de ayuda del sistema para ver si existía documentación sobre este programa. Ejecuté el comando de manual:

**man useless**

- Al abrirse el manual, bajé hasta el final del texto. Allí, en la sección de créditos y autores, estaba escondida la recompensa:

```
**picoCTF{us3l3ss_ch4ll3ng3_3xpl0it3d_4151}**
```

## **Notas adicionales**
- **`wget`**: Descarga archivos directamente desde internet.
- **`ssh`**: Entra por control remoto a otra computadora.
- **`ls`**: Muestra la lista de archivos que tienes en tu carpeta.
- **`chmod +x`**: Convierte un archivo normal en un programa ejecutable.
- **`cat`**: Muestra todo el texto de un archivo en la pantalla.
- **`grep`**: Busca una palabra específica dentro de un montón de texto.
- **`man`**: Abre el manual de instrucciones de un comando o programa.
