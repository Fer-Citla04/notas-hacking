## **Reto**:  interencdec
## **Descripción**
Can you get the real meaning from this file.Download the file [here](https://artifacts.picoctf.net/c_titan/1/enc_flag).
## **Solución**
1. Primero utilicé el comando `cat enc_flag` en la terminal para visualizar el contenido. Identifiqué una cadena con la estructura característica de **Base64** 
2. Durante el proceso, realicé varias iteraciones para limpiar la salida de datos:
`echo YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgyeG9OakJzTURCcGZRPT0nCg== | base64 --decode` 
    Resultado: `b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX2xoNjBsMDBpfQ=='`
    
3. Quité `b'` y las comillas ''
    
4. `echo d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX2xoNjBsMDBpfQ== | base64 --decode` 
    Resultado: `wpjvJAM{jhlzhy_k3jy9wa3k_lh60l00i}`
     
5. Utilicé la herramienta **dCode** para identificar el cifrado, confirmando que se trataba de un **Cifrado César**.

```
picoCTF{caesar_d3cr9pt3d_ea60e00b}  
```

## **Referencias
https://www.dcode.fr/caesar-cipher