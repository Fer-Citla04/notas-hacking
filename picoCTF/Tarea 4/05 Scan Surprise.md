## **Reto**:   Scan Surprise
## **Descripción**
I've gotten bored of handing out flags as text. Wouldn't it be cool if they were an image instead?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_atlas/13/challenge.zip)

Additional details will be available after launching your challenge instance.

## **Solución**
1. Al conectar por SSH, el servidor enviaba un código QR en formato ASCII. 
2. Como el canal de texto era lo único confiable, convertí el archivo binario flag.png en una cadena de texto imprimible.
    `base64 flag.png`
3. Reconstruí el binario redirigiendo la cadena decodificada a un archivo: `echo "BASE64_COPIADO" | base64 -d > flag.png`
4. Una vez con la imagen en local utilicé la suite **ZBar**, que es un estándar en Linux para procesar códigos de barras y QR desde la línea de comandos.
    `sudo apt install zbar-tools`
    `zbarimg local_flag.png`
5. La herramienta procesó los patrones de bits del código QR y extrajo la cadena de texto oculta, revelando la bandera directamente en la terminal.
```
picoCTF{p33k_@_b00_d4ca652e}
```

## **Notas adicionales
**ZBar:** Es extremadamente útil en retos de Forense porque puede leer códigos QR incluso si están rotados, invertidos o tienen ruido digital.
## **Referencias
https://medium.com/@creepus/picoctf-walkthrough-scan-surprise-fd020c6ba0d0