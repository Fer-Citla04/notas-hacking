## **Reto**:  Picker IV
## **Descripción**
Can you figure out how this program works to get the flag?Connect to the program with netcat:`$ nc saturn.picoctf.net 56693`The program's source code can be downloaded [here](https://artifacts.picoctf.net/c/529/picker-IV.c). The binary can be downloaded [here](https://artifacts.picoctf.net/c/529/picker-IV).
## **Solución**
1. En el código fuente del programa existe una función llamada `win()` que no se invoca en ninguna parte del flujo normal de ejecución, pero que contiene la lógica para imprimir la bandera. 
2.  Abrir el binario con el depurador con el comando `gdb picker-IV`
3. Después se listaron las funciones y sus direcciones, dentro de la consola de GDB, se ejecutó el comando `info functions`.
4. En el listado se localizó la función `win`: `0x000000000040129e win`
5. Por último, al conectar al servidor mediante y cuando el programa solicita la dirección, ingresamos el valor obtenido: `40129e`.

```
picoCTF{n3v3r_jump_t0_u53r_5uppl13d_4ddr35535_b8de1af4}
```
