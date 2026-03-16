## **Reto**:  c0rrupt
## **Descripción**
We found this [file](https://challenge-files.picoctf.net/c_fickle_tempest/87bdc8ce30b177d033b3d68bca4647950bb07304032861baa912ebe08701d355/mystery). Recover the flag.

## **Solución**
Al descargar el archivo "mystery", el sistema no lo identificaba como un tipo válido. La pista del reto decía: "trata de preparar el encabezado", lo que indicó que estaba frente a una imagen con la cabecera dañada. Al abrir el archivo en un editor hexadecimal, estaban rastros de que originalmente era un **PNG**, pero sus bytes iniciales estaban mal.

Para reparar el archivo y recuperar la bandera, seguí estos pasos en el editor hexadecimal:

1. **Reparar el encabezado:** Cambié los primeros bytes por los correctos de un PNG: `89 50 4E 47 0D 0A 1A 0A`.
2. **Corregir el chunk IHDR:** El primer fragmento de datos después de la cabecera debe ser **IHDR**, pero el nombre estaba mal escrito. Lo corregí usando los códigos ASCII `49 48 44 52`. Entonces, el archivo ya se reconocía como imagen, pero seguía sin abrirse.
3. **Uso de pngcheck:** Instalé la herramienta `pngcheck` y cambié a `00` para normalizar la imagen.
4. **Reparar el chunk IDAT:** El nombre estaba mal y la longitud era grande. Por lo que cambié el nombre a "IDAT" y ajusté la longitud a algo más lógico, dejando solo `00 00 FF A5`.

Después de esto, se pudo abrir la imagen y visualizar la bandera:

```
**picoCTF{c0rrupt10n_1847995}**
```

## **Notas adicionales
- **Chunks (Fragmentos):** Los archivos PNG se dividen en bloques (IHDR, pHYs, IDAT, IEND). Cada uno tiene un nombre, datos y un código CRC de verificación.
- **pngcheck:** Es una herramienta de terminal para encontrar errores invisibles en la estructura de una imagen.

## **Referencias
https://www.youtube.com/watch?v=7zY4VkiWbBI&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=21