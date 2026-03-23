## **Reto**:   Disk, disk, sleuth!
## **Descripción**
Use `srch_strings` from the sleuthkit and some terminal-fu to find a flag in this disk image.[dds1-alpine.flag.img.gz](https://challenge-files.picoctf.net/c_wily_courier/27cbd6a2ed4a59d600f2a24c1ccaa6de66f9aeee95d6b365160fd75649e45f1b/dds1-alpine.flag.img.gz)

## **Solución**
Para este reto, se nos proporcionó una imagen comprimida.
1. El archivo venía con extensión `.gz`, por lo que utilicé el comando `gunzip` para extraer la imagen de disco original: `gunzip dds1-alpine.flag.img.gz`
2. El reto sugería usar `srch_strings`.
3. Para no leer muchas líneas de texto basura, combiné la salida de la herramienta con un `grep` para buscar directamente la bandera: `srch_strings dds1-alpine.flag.img | grep "picoCTF"`
    
Al ejecutar el comando, localizó la cadena de texto que contenía la bandera:

```
 picoCTF{f0r3ns1c4t0r_n30phyt3_5e56e786}
```

## **Notas adicionales**
 - A diferencia de un archivo normal, una imagen de disco (`.img`) es una copia bit por bit de un sistema de archivos completo, lo que requiere herramientas especializadas para su análisis.
- `srch_strings`es una herramienta parte de **The Sleuth Kit (TSK)** y es muy potente porque, a diferencia del comando `strings` común, puede analizar sectores del disco que el sistema operativo ya no reconoce como archivos activos.
