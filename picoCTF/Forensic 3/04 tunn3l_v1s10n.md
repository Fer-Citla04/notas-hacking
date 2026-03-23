## **Reto**:  tunn3l_v1s10n
## **Descripción**
We found this file. Recover the flag.[tunn3l_v1s10n](https://challenge-files.picoctf.net/c_wily_courier/626df9feed926c1e1280804f5d87fde5576e266ff250a819a5528b0471b0f3f7/tunn3l_v1s10n)

## **Solución**
Primero descargué el archivo.

1. Luego, al abrir el archivo en hexadecimal, vi que los primeros dos bytes eran `42 4D`. 
2. 
- **Offset 0E:** El tamaño del encabezado debe ser de 40 bytes para un BMP de Windows. En el archivo aparecía un valor incorrecto ("BAD"), así que lo cambié por `28` (40 en hexadecimal).
- **Offset 0A:** Aquí debe ir el offset donde comienzan los datos de la imagen. Lo corregí para que coincidiera con la estructura estándar.

3. Después de corregir el encabezado, la imagen por fin abrió, pero solo mostraba una parte que decía "not a flag". Esto significa que la imagen es más grande de lo que estamos viendo, pero sus dimensiones están "recortadas" en el código.
    
4. 
- Fui al **offset 12** (ancho) y **offset 16** (alto).
- El ancho estaba bien, pero el alto estaba limitado. Incrementé el valor del alto en el editor hexadecimal.
3. **Obtención de la bandera:** Al aumentar el alto de la imagen, la ventana se expandió y reveló la bandera 

```
picoCTF{qu1t3_a_v13w_2020}
```


## **Referencias
https://www.youtube.com/watch?v=1ucy2G1PIh4&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=27