## **Reto**:  Sleuthkit Apprentice.
## **Descripción**
Download this disk image and find the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download compressed disk image](https://artifacts.picoctf.net/c/137/disk.flag.img.gz)

## **Solución**
1. Descomprimí la imagen con `gzip -d disk.flag.img.gz`.
2. Utilicé `mmls disk.flag.img` para obtener la tabla de particiones. Identifiqué que la partición principal de Linux comenzaba en el **offset 2048**.
3. Verifiqué el tipo de sistema de archivos con el comando `fsstat -o 2048 disk.flag.img`. Esto confirmó que la partición estaba usando un formato compatible (como ext4).
4. Usé el comando `fls` para listar los archivos de forma recursiva. Para agilizar la búsqueda de la bandera, filtré los resultados con `grep`: `fls -r -o 2048 disk.flag.img | grep -i "flag"`

- Encontré un archivo llamado `flag.uni.txt`. Note que algunos archivos tenían un asterisco (`*`), lo que indica en forense que el archivo fue marcado como eliminado pero su estructura de metadatos (inodo) aún es visible.
  
5. Una vez identificado el número asociado a `flag.uni.txt`, utilicé la herramienta `icat` para leer el contenido directamente desde el inodo, saltándome la restricción del sistema de archivos que lo marcaba como "borrado": `icat -o 2048 disk.flag.img [Número_de_Inodo]`

```
picoCTF{by73_5urf3r_adac6cb4}
```

## **Notas adicionales
- **Inodo (Inode):** Es una estructura de datos que almacena la información de un archivo (tamaño, dueño, permisos) y, lo más importante, en qué bloques del disco están sus datos reales.
- **fls:** Esta herramienta lista los archivos y directorios en una imagen. Es muy útil porque puede mostrar archivos que ya no aparecen en el explorador de archivos normal.
