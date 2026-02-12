## **Reto**: 9 -> Big zip

## **Descripción**
Unzip this archive and find the flag.

- [Download zip file](https://artifacts.picoctf.net/c/504/big-zip-files.zip)

## **Solución**
- El primer paso fue "abrir la caja" para ver qué había dentro. Para ello, usé el comando de descompresión:

**unzip big-zip-files.zip 

- Al descomprimirlo, se creó una carpeta llena de muchos archivos y subcarpetas. En lugar de entrar una por una, utilicé el comando para listar y confirmar que la estructura era demasiado grande para una búsqueda manual:
**ls -R**

- Sabiendo que la bandera siempre empieza con la palabra "pico", utilicé el comando de búsqueda recursiva. Este comando es como enviar un sabueso que entra en todas las habitaciones de una mansión al mismo tiempo:

**grep -R "pico" ***

Y así obtuve la bandera
```
picoCTF{gr3p_15_m4g1c_ef8790dc}
```

## **Notas adicionales**
- **unzip**: Abre archivos comprimidos `.zip` y extrae su contenido.
- **ls -R**: Muestra todos los archivos, incluyendo los que están dentro de carpetas (recursivo).
- **grep**: Busca una cadena de texto específica dentro de un archivo.
- **-R**: Opción que obliga a `grep` a buscar dentro de todas las carpetas y subcarpetas.