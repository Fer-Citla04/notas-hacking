## **Reto**:  m00nwalk
## **Descripción**
Decode this [message](https://challenge-files.picoctf.net/c_fickle_tempest/816c75fc4b45dfc4ab4c4caad4ac738a3e0cfb3825fedda2a753eb5360c477bb/message.wav) from the moon.

## **Solución**
Al descargar el archivo del reto, se encontró con un audio en formato `.wav`. Al principio intenté usar el comando `strings` y revisar el espectrograma del audio, pero no encontré nada. 

1. Instalé una herramienta en la terminal para decodificar este tipo de señales. Utilicé un repositorio de GitHub que permite transformar el audio a imagen.
2. Ejecuté el siguiente comando para procesar el audio y generar la imagen:
`sstv -d message.wav result.png`

Al ejecutarlo, la herramienta detectó automáticamente el formato "scotty" y empezó a reconstruir la imagen. El resultado fue un archivo `.png` que venía rotado, pero al girarlo a la derecha en el visor de imágenes de Kali Linux, se podía leer claramente la bandera:

```
**picoCTF{beep_boop_im_in_space}**
```

## **Notas adicionales
- **SSTV (Slow Scan TV):** Es un método de transmisión de imágenes utilizado en misiones espaciales
- **Scotty:** Es uno de los modos de transmisión de SSTV. 
- **sstv (herramienta):** Es un script de Python que procesa las frecuencias del audio y las traduce a píxeles de color para formar una imagen.

## **Referencias
https://www.youtube.com/watch?v=UyLTEpAz6eE&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=19