## **Reto**:  extensions
## **Descripción**
This is a really weird text file. Can you find the flag?Get the flag from [TXT](https://challenge-files.picoctf.net/c_fickle_tempest/31fe772e6a4c71e867af0b2a93818e06d8f8ebf8af2a9615495d00356ff576da/flag.txt).
## **Solución**
Al descargar el archivo del reto, noté que tenía el nombre `flag.txt.

Al usar el comando `file flag.txt` en la terminal, Linux me indicó que en realidad era una **imagen PNG**. Esto sucede porque el sistema operativo no solo se fija en el nombre, sino en los **Magic Bytes** que están en la cabecera del código binario.
Para confirmar esto, utilicé el comando `xxd` para ver el contenido hexadecimal del archivo:

`xxd flag.txt | head`

Encontré la firma `89 50 4e 47 0d 0a 1a 0a`, que corresponde a los archivos PNG. Como el archivo estaba "disfrazado" de texto, lo único que tuve que hacer fue corregir su extensión con el comando `mv`:

`mv flag.txt flag.png`

Al cambiarle el nombre, el sistema ya pudo reconocerlo correctamente como una imagen. Abrí el archivo `flag.png` y en la imagen aparecía escrita la bandera. 

```
picoCTF{now_you_know_about_extensions}
```
## **Referencias
https://www.youtube.com/watch?v=FbFpIS60M_s&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=17