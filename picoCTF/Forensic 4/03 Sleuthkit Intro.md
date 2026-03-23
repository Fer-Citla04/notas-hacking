## **Reto**:  Sleuthkit Intro.
## **Descripción**
Download the disk image and use `mmls` on it to find the size of the Linux partition. Connect to the remote checker service to check your answer and get the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.[Download disk image](https://artifacts.picoctf.net/c/164/disk.img.gz)Access checker program: `nc saturn.picoctf.net 51346`
## **Solución**
1. El archivo descargado era `disk.img.gz`. Primero verifiqué su tipo con `file disk.img.gz`.
2. Descomprimí el archivo para obtener la imagen: `gzip -d disk.img.gz`.
3. Utilicé la herramienta `mmls` sobre el archivo disk.img->  `mmls disk.img` 
4. El comando mostró la estructura del disco, indicando que los sectores son de **512 bytes**.
5. Localicé la fila con la descripción **"Linux (0x83)"**.
6. Al observar la columna **Length**, identifiqué el valor: **202752**. Este número representa la cantidad de sectores que ocupa esa partición.
7. Me conecté al servicio usando Netcat: `nc saturn.picoctf.net 52279`.
8. El sistema me preguntó por el tamaño de la partición en sectores.
9. Ingresé el valor **202752** y me entregó la bandera:
   
```
picoCTF{mm15_f7w!}
```
## **Notas adicionales**
- **mmls :** Es una herramienta que muestra el diseño de las particiones en un volumen de almacenamiento. Es vital para saber dónde empieza cada sistema de archivos antes de intentar montarlos o analizarlos.
