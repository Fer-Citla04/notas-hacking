## **Reto**:  Milkslap.
## **Descripción**
🥛

http://wily-courier.picoctf.net:54146/

## **Solución**
Al entrar al enlace del reto, me encontré con una página que muestra una imagen. Al mover el ratón, parece que le das una cachetada a la persona en la foto. 
Entonces al analizar la imagen que genera la animación.

1. Identifiqué la URL de la imagen en el código fuente del sitio y la descargué usando `wget`.
2.  Ejecuté la herramienta para buscar datos ocultos en los diferentes canales de la imagen, los bits menos significativos `zsteg -a image.png`

3. `zsteg` detectó una cadena de texto incrustada en los metadatos. La cadena incluía un carácter `\n` al final, que simplemente representa un salto de línea y no forma parte de la bandera.

```
picoCTF{imag3_m4n1pul4t10n_sl4p5}
```

## **Notas adicionales
`gem install zsteg`
- zsteg vs steghide:** Es fundamental elegir la herramienta correcta según el formato. `zsteg` es la opción más potente para archivos PNG y BMP porque analiza técnicas de LSB  de forma automática.
