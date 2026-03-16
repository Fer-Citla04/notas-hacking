## **Reto**:   WhitePages
## **Descripción**
I stopped using YellowPages and moved onto WhitePages... but [the page they gave me](https://challenge-files.picoctf.net/c_fickle_tempest/f35d2be8de731d412d3dbd8c79e6c5b32c62efbb124cf319f54ebddf76ea0ffe/whitepages.txt) is all blank!

## **Solución**

Al abrir el archivo del reto, aparentemente no había nada y el comando `cat` no mostraba información. Pero al revisar la longitud del archivo, tenía 2,964 caracteres.

Al ejecutar el comando `file`, era un archivo **Unicode con codificación UTF-8**. Para entender qué estaba pasando, examiné el archivo en hexadecimal y encontré dos patrones que se repetían todo el tiempo: `e2 80 83` y `20`.  `e2 80 83` es un carácter Unicode que representa un espacio en blanco y el `20` es el espacio normal.

Para resolverlo, se utilizó un script de Python con la librería **Pwntools** para hacer el reemplazo:

`from pwn import *`

`Se abre el archivo en formato de lectura de bytes`
`with open('whitepages.txt', 'rb') as file:`
    `data = file.read()`

`Reemplazamos el espacio Unicode por '0' y el normal por '1'`
`data = data.replace(b'\xe2\x80\x83', b'0')`
`data = data.replace(b' ', b'1')`

 `Quitamos espacios extras y convertimos de binario a texto`
`data = data.strip()`
`print(unbits(data))`


Al final, el script transformó todos esos espacios en una cadena de ceros y unos, y al decodificarla a ASCII, nos dió la bandera:

```
picoCTF{not_all_spaces_are_created_equal_f6166971531e3ad3b35138611330bba8}
```
## **Notas adicionales

- **UTF-8:** Es un esquema de codificación que permite representar casi todos los lenguajes del mundo. Aquí se usó para esconder bits usando espacios diferentes.
- **e2 80 83:** Es el valor hexadecimal de un espacio "especial" que se ve exactamente igual a uno normal, lo que permitía que el archivo pareciera vacío.
- **unbits:** Es una función de Python (de Pwntools) que facilita mucho el trabajo porque convierte directamente los grupos de 8 bits (ceros y unos) en caracteres legibles.
## **Referencias
https://www.youtube.com/watch?v=427HDV7tzow&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=21