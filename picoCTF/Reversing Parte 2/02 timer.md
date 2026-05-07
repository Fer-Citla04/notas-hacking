## **Reto**:  timer
## **Descripción**
You will find the flag after analysing this apkDownload [here](https://artifacts.picoctf.net/c/449/timer.apk).
## **Solución**
1. Primero, descargué el archivo proporcionado. 
2. Basándome en las pistas del reto que sugerían realizar una descompilación, utilicé la herramienta **apktool** en Kali para revertir el empaquetado del archivo y poder acceder a su estructura interna `apktool d timer.apk`
3. Luego, utilicé el comando `grep` con el parámetro `-r` para realizar una búsqueda de la cadena "pico" en todo el directorio `grep -r "pico"` 
4. El comando localizó la bandera almacenada como el valor de `versionName` dentro del archivo de configuración `apktool.yml` 

```
picoCTF{t1m3r_r3v3rs3d_succ355fully_17496}
```
## **Notas adicionales
- **APK**: Es un archivo comprimido que contiene el código ejecutable (DEX), recursos y metadatos de una aplicación Android.