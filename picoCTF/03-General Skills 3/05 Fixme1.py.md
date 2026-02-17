## **Reto**: 5-> fixme1.py

## **Descripción**
Fix the syntax error in this Python script to print the flag.[Download Python script](https://artifacts.picoctf.net/c/27/fixme1.py)
## **Solución**
- Primero, se descarga el archivo  y se trata de ejecutar para ver qué está fallando:

`wget https://artifacts.picoctf.net/c/27/fixme1.py`
`python3 fixme1.py`
- Luego, se abre el archivo con un editor de texto en la terminal: `nano fixme1.py`
- Se debe eliminar los espacios al principio de esa línea para que esté alineada a la izquierda, igual que el resto del código. Para guarda los cambios se presiona **Ctrl + O**, luego **Enter** y después **Ctrl + X** para salir y se vuelve a correr el programa.
- Así es como se consigue la bandera
`picoCTF{1nd3nt1ty_cr1515_182342f7}`
## **Notas adicionales**
- **nano**: Es un editor de texto dentro de la terminal. Que permite modificar archivos sin salir de la consola.
- **IndentationError**: Un error específico de Python que ocurre cuando el código no está alineado correctamente.
- **Ctrl + O / Ctrl + X**: Comandos de teclado para guardar y cerrar archivos en el editor nano.

