## **Reto**:  Operation Orchid
## **Descripción**
Download this disk image and find the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download compressed disk image](https://artifacts.picoctf.net/c/214/disk.flag.img.gz)

## **Solución**
1. Trabajé en el directorio `/tmp` del Webshell para optimizar el espacio.
2. Descomprimí la imagen: `gunzip disk.flag.img.gz`.
3. Usé `mmls disk.flag.img` para localizar los puntos de inicio (offsets). Identifiqué dos particiones Linux, siendo la más prometedora la que inicia en el **offset 411648**.
4. Listé los archivos de la partición con `fls -o 411648 disk.flag.img`.
5. Encontré una carpeta `root` (inodo 472). Al explorar dentro de ella (`fls -o 411648 disk.flag.img 472`), localicé el archivo **`flag.txt.enc`** en el inodo 1782.
6. La extensión `.enc` indicaba que el archivo estaba cifrado. Al intentar leerlo con `icat`, los primeros bytes mostraban `Salted__`, una firma típica de archivos cifrados con **OpenSSL**.
7. Para encontrar la contraseña, analicé las cadenas de texto en todo el disco que mencionaran el archivo de la bandera: `strings -t d disk.flag.img | grep flag.txt`
8. El resultado reveló el comando que se utilizó originalmente para cifrar el archivo: se usó **AES-256-CBC** con la contraseña: **`unbreakablepassword1234567`**.
9. Primero extraje el archivo cifrado a mi directorio actual: `icat -o 411648 disk.flag.img 1782 > flag.txt.enc`
10. Luego, utilicé OpenSSL para revertir el cifrado usando la clave encontrada: `openssl aes-256-cbc -d -in flag.txt.enc -out flag.txt -k unbreakablepassword1234567 -md sha256`

Al abrir el nuevo archivo `flag.txt`, la bandera apareció correctamente.

```
picoCTF{h4un71ng_p457_1d02081e}
```
## **Notas adicionales**
- **Archivos .enc y Salted__:** La "sal" (salt) en criptografía son datos aleatorios que se añaden antes de cifrar para asegurar que el mismo texto plano no genere siempre el mismo texto cifrado.
- **strings -t d:** El parámetro `-t d` es vital en forense porque te da el offset exacto en bytes decimales, permitiéndote saber en qué parte física del disco se encontraba esa cadena de texto.