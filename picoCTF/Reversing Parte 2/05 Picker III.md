## **Reto**:  Picker III
## **Descripción**
Can you figure out how this program works to get the flag?Connect to the program with netcat:`$ nc saturn.picoctf.net 50640`The program's source code can be downloaded [here](https://artifacts.picoctf.net/c/526/picker-III.py).
## **Solución**
1. Primero, analizamos el código fuente del programa, el cual implementa un entorno restringido. El sistema permite realizar cuatro operaciones predefinidas: `print_table`, `read_variable`, `write_variable` y `getRandomNumber`. El objetivo es lograr que el programa ejecute una función oculta llamada `win()`, la cual imprime la bandera.
2. Identificamos que el programa utiliza una tabla de funciones (`func_table`) que es, en realidad, una única cadena de caracteres mutable de 128 bytes. Esta tabla está dividida en cuatro entradas de 32 bytes cada una:
-  `print_table` (0-31)
- `read_variable` (32-63)
- `write_variable` (64-95)
- `getRandomNumber` (96-127)

3. La vulnerabilidad reside en la función `write_variable()`. Cuando el usuario selecciona una opción del menú, el programa extrae el nombre de la función desde esta tabla y lo ejecuta usando `eval(func_name + '()')`.
4. Para explotar esto, preparamos un payload que sobrescribiera la última entrada de la tabla con el nombre de la función `win`. Fue importante que la cadena resultante mantenga la longitud de 128 bytes para no corromper la estructura de la memoria del programa.
5. Al modificar la variable `func_table` con el payload, la estructura interna cambió de: `...write_variable getRandomNumber` a: `...write_variable win`
6. Finalmente, seleccionamos la opción 4 en el menú del programa. En lugar de ejecutar la función original para obtener un número aleatorio, el comando `eval()` procesó la nueva entrada de la tabla, ejecutando `win()` 

```
picoCTF{7h15_15_wh47_w3_g37_w17h_u53r5_1n_ch4rg3_226dd285}
```
## **Notas adicionales**
- **Alineación de Memoria**: El reto requiere un control preciso del espacio en blanco (padding) para asegurar que el nombre de la función `win` quede exactamente en la posición que el programa lee para la opción 4.