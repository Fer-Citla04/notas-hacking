## **Reto**:  Safe Opener 2
## **Descripción**
What can you do with this file?I forgot the key to my safe but this [file](https://artifacts.picoctf.net/c/287/SafeOpener.class) is supposed to help me with retrieving the lost key. Can you help me unlock my safe?
## **Solución**
1. Primero descargué el archivo con `wget`
2. El archivo era un `.class` que contiene **bytecode** de Java. Este formato no es legible directamente como un archivo de texto `.java`. Intentar leerlo con `cat` mostraría caracteres extraños.
3. Dado que las banderas suelen guardarse como cadenas de texto, utilicé una herramienta diseñada para encontrar texto legible dentro de archivos binarios con el comando `strings SafeOpener.class | grep "picoCTF"`

```
┌──(kali㉿kali)-[~/Documentos/safeOpener2]
└─$ strings SafeOpener.class | grep "picoCTF"
,picoCTF{SAf3_0p3n3rr_y0u_solv3d_it_b427942b}
```


```
 picoCTF{SAf3_0p3n3rr_y0u_solv3d_it_b427942b}
```
## **Notas adicionales
- **`strings`**: Escanea el archivo binario y extrae cualquier secuencia de caracteres imprimibles.
- **`|` (pipe)**: Toma la salida de `strings` y se la pasa al siguiente comando.
- **`grep "picoCTF"`**: Filtra todas las cadenas encontradas y solo muestra la que contiene el prefijo de la bandera.