## **Reto**: 10 -> 10 Serpentine

## **Descripción**
Find the flag in the Python script![Download Python script](https://artifacts.picoctf.net/c/37/serpentine.py)
## **Solución**
- Primero, se descarga el script y se intenta ejecutar para ver cómo funciona el menú:
 `wget https://artifacts.picoctf.net/c/37/serpentine.py`
  `python serpentine.py`

- Al elegir la opción **b**, el programa nos dice que la función `print_flag` está perdida. Entonces, abrimos el archivo con el editor para corregirlo: `nano serpentine.py`
- Se debe bajar hasta el final del archivo, donde está la función `main()`. Buscamos la línea que dice `elif choice == 'b':`. Veremos que solo tiene un `print` con un mensaje de error.
- Debemos borrar ese mensaje o añadir debajo la llamada a la función real. La línea debe quedar exactamente así (respetando los espacios de la izquierda):

`elif choice == 'b':`
  `print_flag()`

- Para guardar los cambios se presiona **Ctrl + O**, luego **Enter** y después **Ctrl + X** para salir. Finalmente, se vuelve a correr el programa y al presionar la **b**, el script ahora sí llamará a la función que descifra la bandera.
- Así es como se consigue la bandera: 
```
picoCTF{7h3_r04d_l355_7r4v3l3d_8e47d128}
```
