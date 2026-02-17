## **Reto**: 6 -> fixme2.py

## **Descripción**
Fix the syntax error in the Python script to print the flag.[Download Python script](https://artifacts.picoctf.net/c/6/fixme2.py)

## **Solución**
- Primero, se descarga el archivo y se trata de ejecutar para identificar el error de sintaxis:
`wget https://artifacts.picoctf.net/c/5/fixme2.py` `python3 fixme2.py`
- Luego, se abre el archivo con el editor de texto en la terminal para revisar la lógica: `nano fixme2.py`
- Se debe buscar la línea del `if` que tiene un solo signo de igual (`if flag = ""`). Se corrige agregando otro signo de igual para que sea una comparación (`if flag == ""`), ya que en Python para comparar se usa doble igual.
- Para guardar los cambios se presiona **Ctrl + O**, luego **Enter** y después **Ctrl + X** para salir. Finalmente, se vuelve a correr el programa.
- Así es como se consigue la bandera:

`picoCTF{3qu4l1ty_n0t_4551gnm3nt_f6a5aefc}`
## **Notas adicionales**
- if flag == "": Es una pregunta lógica. El doble igual == le pregunta a la computadora: "¿Es el valor de la bandera igual a nada?". Si se usa solo uno =, la computadora se confunde porque cree que se está intentando guardar un vacío en la bandera en lugar de comparar.

