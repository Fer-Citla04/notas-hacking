## **Reto**: 10 -> First Find

## **Descripción**
Unzip this archive and find the file named 'uber-secret.txt'

- [Download zip file](https://artifacts.picoctf.net/c/501/files.zip)
## **Solución**
- Primero, utilicé la herramienta de descarga para traer el archivo comprimido desde los servidores de picoCTF a mi terminal.

**wget [https://artifacts.picoctf.net/c/502/files.zip](https://www.google.com/search?q=https://artifacts.picoctf.net/c/502/files.zip)**

- En lugar de descomprimirlo primero, intenté leer el contenido del archivo `.zip` directamente. Como los archivos comprimidos están en un formato no podemos leer, la pantalla se llenó de símbolos extraños y "basura".
**cat files.zip**

- Para limpiar el desastre de símbolos extraños, utilicé una herramienta que extrae solo las cadenas de texto. Luego, conecté ese resultado con un buscador para encontrar la bandera directamente dentro del archivo comprimido.

**strings files.zip | grep pico**

```
picoCTF{f1nd_15_f457_ab443fd1}
```

## **Notas adicionales**
- **wget**: Descarga archivos de internet mediante una URL.
- **cat**: Intenta mostrar el contenido de un archivo.
- **strings**: Una herramienta que ignora los símbolos raros de un archivo y solo te muestra las palabras y frases legibles.
- **grep**: Busca una palabra específica (en este caso "pico") dentro del texto que le entrega el comando anterior.