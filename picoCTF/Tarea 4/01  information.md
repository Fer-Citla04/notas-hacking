## **Reto**:  information
## **Descripción**
Files can always be changed in a secret way. Can you find the flag?[cat.jpg](https://challenge-files.picoctf.net/c_wily_courier/76e95e3e6ee69b4f82b3cea25051f5a9a5918b57809a1f90b29b06b776c73bc7/cat.jpg)
## **Solución**
1. El reto sugería que el archivo fue modificado de forma secreta. En un archivo de imagen cat.jpg, esto apunta a que los datos están integrados en la estructura del archivo.
2. Utilicé ExifTool, la herramienta estándar para manipular metadatos. 
   `exiftool cat.jpg`
3. Encontré que el campo License contenía una cadena: `cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9`
4. Procedí a revertir la codificación Base64 con el comando
    `echo "cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9" | base64 -d`
    
Y así fue como se encontró la bandera:

```
picoCTF{the_m3tadata_1s_modified}
```
