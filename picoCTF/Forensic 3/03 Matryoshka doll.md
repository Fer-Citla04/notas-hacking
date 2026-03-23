## **Reto**:  Matryoshka doll
## **Descripción**
Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one?Image: [dolls.jpg](https://challenge-files.picoctf.net/c_wily_courier/1709f471bed1c90c7b343b2d6a4f0d1257abed9ef467457d6438adb71be0b37c/dolls.jpg)

## **Solución**
Para este reto, descargué una imagen llamada `dolls.jpg`. 

Para resolverlo, utilicé la herramienta **Binwalk**.

1. Ejecuté `binwalk dolls.jpg` y dentro de la imagen JPG había un archivo comprimido que contenía otra imagen.
2. **Extracción recursiva:** Utilicé el comando `binwalk -e dolls.jpg` para extraer el contenido. Esto creó una carpeta llamada `_dolls.jpg.extracted`.
3. Al entrar en las carpetas extraídas, encontré una nueva imagen de una matrioska más pequeña. Repetí el análisis y la extracción varias veces:
- `2_c.jpg` contenía a `3_c.jpg`.
- `3_c.jpg` contenía a `4_c.jpg`.
- Dentro de la última imagen, Binwalk detectó un archivo llamado `flag.txt`.
1. Por último con `cat flag.txt` fue como se consiguió la bandera.


```
picoCTF{LL9lb1dR4QbGe4l4iWCvGq9pdtwt7392}
```

## **Referencias
https://www.youtube.com/watch?v=NkbtA7x5aVI&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=26