## **Reto**: 7 -> Magikarp Ground Mission

## **Descripción**
Do you know how to move between directories and read files in the shell? Start the container, `ssh` to it, and then `ls` once connected to begin.Login via `ssh` as `ctf-player` with the password, `8c606eb1` on the host `wily-courier.picoctf.net` and port `63273`.
## **Solución**
- Primero me conecté al servidor remoto usando el usuario **ctf-player** y el puerto **63273**. Al ser la primera vez que entraba a este host, tuve que confirmar que confiaba en él escribiendo "yes" y luego ingresé la contraseña **8c606eb1**.

**ssh ctf-player@wily-courier.picoctf.net -p 63273**

- Luego al entrar revisé mi ubicación actual y encontré dos archivos. Leí el primero y obtuve el inicio de la bandera. El segundo archivo me dio la pista para encontrar la siguiente parte.

**ls** **cat 1of3.flag.txt** **cat instructions-to-2of3.txt**

- La pista decía que fuera al "origen de todas las cosas" (**/**). Me moví hacia esa ubicación y busqué qué había allí. Encontré la segunda parte de la bandera y una nueva instrucción para la parte final.

**cd /** **ls** **cat 2of3.flag.txt** **cat instructions-to-3of3.txt**

- Por último, regresé a mi carpeta personal para buscar la pieza que faltaba. Leí el último archivo y así completé la bandera completa.

**cd ~** **ls** **cat 3of3.flag.txt**

```
picoCTF{xxsh_0ut_0f_//4t3r_0b24fc4f}
```

## **Notas adicionales**
- **ssh**: Crear la conexión segura para entrar al servidor remoto.
- **ls**: Listar los archivos para saber qué hay en la carpeta actual.
- **cat**: Leer el contenido de los archivos de texto para ver las pistas y banderas.
- **cd**: Cambiar de una carpeta a otra (moverse por el sistema).
- **pwd**: Confirmar en qué carpeta estaba parado en ese momento.
- **cd /**: Ir directamente a la carpeta raíz (la base de todo el sistema).
- **cd ~**: Regresar rápidamente a mi carpeta personal de usuario.