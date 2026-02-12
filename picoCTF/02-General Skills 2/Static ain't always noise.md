## **Reto**: 4 -> Static ain't always noise

## **Descripción**
Can you look at the data in this binary? The bash script might help! [static](https://challenge-files.picoctf.net/c_wily_courier/b6c2dd492eb053dfbb3fcfa9eb142c8d11f6a00c0691031fc92b045d65b6e56a/static), [ltdis.sh](https://challenge-files.picoctf.net/c_wily_courier/b6c2dd492eb053dfbb3fcfa9eb142c8d11f6a00c0691031fc92b045d65b6e56a/ltdis.sh)

## **Solución**
- Lo primero que hice fue descargar los archivos del reto directamente a mi entorno de trabajo. Necesitaba el binario que contiene el secreto y el script de ayuda proporcionado por picoCTF.

`wget https://challenge-files.picoctf.net/c_wily_courier/.../static`
`wget https://challenge-files.picoctf.net/c_wily_courier/.../ltdis.sh`
- Al intentar ejecutar el script `ltdis.sh`, recordé que los archivos descargados no suelen tener permisos de ejecución por defecto. Así que le otorgué los permisos necesarios con 
`chmod +x ltdis.sh`

- Ejecuté el script sobre el binario. Mi objetivo aquí era descomponer el archivo para ver qué información útil podía extraer, ya que a simple vista un binario es ilegible.
`./ltdis.sh static`

- El script hizo el trabajo pesado por mí: desensambló el código y extrajo todas las cadenas de texto (strings), guardándolas en un archivo nuevo llamado `static.ltdis.strings.txt`.
- Con las cadenas de texto ya extraídas, no quise leer las miles de líneas manualmente. Utilicé `grep` para filtrar el contenido y buscar la palabra clave "pico", que es el formato estándar de las banderas en esta plataforma.

`cat static.ltdis.strings.txt | grep pico`

- Al ejecutar ese último comando, la terminal me devolvió exactamente lo que buscaba:
- 
```
picoCTF{d15a5m_t34s3r_20335e41}
```

