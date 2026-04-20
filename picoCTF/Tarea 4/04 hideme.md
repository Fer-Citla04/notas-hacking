## **Reto**:  hideme
## **Descripción**
Every file gets a flag.The SOC analyst saw one image been sent back and forth between two people. They decided to investigate and found out that there was more than what meets the eye [here](https://artifacts.picoctf.net/c/259/flag.png).
## **Solución**
1. Utilicé **Binwalk**  `binwalk flag.png`
2. Para acceder al contenido del Zip, realicé un proceso de "tallado" o extracción de archivos.
   `binwalk -e flag.png`
3. Exploré la jerarquía de carpetas recuperadas. El reto aplicó una técnica de confusión visual usando el mismo nombre de archivo.
   `secret/flag.png`
4. Finalmente, visualicé la imagen extraída para obtener la bandera.
    `display secret/flag.png`

```
picoCTF{Hiddinng_An_imag3_within_@n_ima9e_cda72af0}
```
