## **Reto**:  So Meta
## **Descripción**
Find the flag in this [picture](https://challenge-files.picoctf.net/c_fickle_tempest/5a0c9a73ac940fb0369275fcf8600f02af2e8d732dd178e19ed8ea8f223d65db/pico_img.png).
## **Solución**
Para este reto, descargué la imagen del reto `pico_img.png`. La pista del reto preguntaba si sabía qué significaba "meta" en el contexto de los archivos.
Los metadatos son datos que describen otros datos
Y para resolverlo se utilizó una herramienta llamada `exiftool`, que sirve para leer y escribir meta-información en archivos. Y la ejecuté con el archivo del reto:

`exiftool pico_img.png`

Al revisar el listado de información, se reflejó en el campo llamado **"Artist"** la bandera, pero se podía especificar más:

`exiftool -Artist pico_img.png`

```
picoCTF{s0_m3ta_ba6c953a}
```
## **Referencias
https://www.youtube.com/watch?v=Govu_p-wf4I&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=15