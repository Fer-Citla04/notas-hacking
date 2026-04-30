## **Reto**: HideToSee  
## **Descripción**
How about some hide and seek heh?Look at this image [here](https://artifacts.picoctf.net/c/241/atbash.jpg).
## **Solución**
1. Se utilizó el comando `file` para confirmar que `atbash.jpg` era un formato JPEG válido y el comando `strings` para buscar cadenas de texto como "pico" en el código, pero al no obtener resultados, se determinó que la información estaba oculta mediante técnicas de esteganografía avanzadas.
2. Se utilizó Steghide Realizamos la inspección con el comando 
   `steghide info atbash.jpg`, dejando la contraseña en blanco, lo que permitió confirmar la existencia de un archivo embebido llamado `encrypted.txt`. 
3. Extraemos

`steghide extract -sf atbash.jpg`

4. Tras extraer el archivo y leer su contenido con `cat encrypted.txt`, obtuvimos la siguiente cadena cifrada:

`krxlXGU{zgyzhs_xizxp_7142uwv9}`

 5. Pegamos la bandera en Atbash para obtener la bandera

```
picoCTF{atbash_crack_7142fde9}
```

## **Referencias**
https://rumkin.com/tools/cipher/atbash/