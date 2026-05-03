## **Reto**:  morse-code
## **Descripción**
Morse code is well known. Can you decrypt this?Download the file [here](https://artifacts.picoctf.net/c/79/morse_chal.wav).Wrap your answer with picoCTF{}, put underscores in place of pauses, and use all lowercase.
## **Solución**
1. Con `wget` se hizo la descarga, verificamos la integridad del archivo `morse_chal.wav` en el directorio de trabajo. Al identificar que se trataba de un formato de audio, determinamos que la bandera estaba codificada mediante código morse.
2. Subimos el audio a la página morsecode.world. La herramienta tradujo el audio a `WH47 H47H 90D W20U9H7`

![[Pasted image 20260503145153.png]]

```
picoCTF{wh47_h47h_90d_w20u9h7}
```
## **Referencias**
https://morsecode.world/international/decoder/audio-decoder-adaptive.html