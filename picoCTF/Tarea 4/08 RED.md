## **Reto**:  RED
## **Descripción**
RED, RED, RED, REDDownload the image: [red.png](https://challenge-files.picoctf.net/c_verbal_sleep/831307718b34193b288dde31e557484876fb84978b5818e2627e453a54aa9ba6/red.png)

## **Solución**
1. Primero, abrí el archivo de imagen para una inspección. La imagen, como sugiere el nombre, era simplemente un cuadro de color rojo. 
2. Para investigar más a fondo, utilicé **zsteg**. Esta herramienta es capaz de analizar los canales de color y extraer información de los bits menos significativos.
3. Teniendo en cuenta lo anterior, ejecuté el siguiente comando en la terminal para realizar un escaneo de todas las técnicas posibles: `zsteg -a red.png`
4. Al revisar los resultados, la herramienta detectó una cadena sospechosa que parecía estar codificada en **Base64**: `cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==`
5. Por último, inserté esta cadena a CyberChef. 
```
picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}
```

## **Referencias
https://medium.com/@erichdryn/red-picoctf-writeup-515376dc78c2
https://gchq.github.io/CyberChef/