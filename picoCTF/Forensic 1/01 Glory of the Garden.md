## **Reto**:  Glory of the Garden
## **Descripción**
This file contains more than it seems.Get the flag from [garden.jpg](https://challenge-files.picoctf.net/c_fickle_tempest/b67cf664cdf2557bea4f1d6079bc099037bc6ea5322afbfc80c5dcf4440c5e7d/garden.jpg).
## **Solución**
Al abrir el link del reto, descargué una imagen llamada `garden.jpg`. La descripción decía: "este jardín contiene más de lo que parece", lo que dio una pista de que había información oculta. Al abrir la imagen, solo se ve un jardín, por lo que no es un error de visualización, sino que la bandera está escondida en los datos binarios.

 Un editor hexadecimal nos permite ver los bytes reales de un archivo sin que un programa los interprete como imagen. Se usó el comando `hexeditor garden.jpg` en terminal. Dentro del editor, utilicé la función de búsqueda (**Ctrl + W**) para buscar la palabra clave "picoCTF".

El editor llevó hasta el final del archivo, donde los bytes ya no forman parte de la imagen. 
Y ahí se pudo observar la bandera

```
picoCTF{more_than_m33ts_the_3y398ee229a}
```

## **Notas adicionales
Otra manera de resolverlo:
Como la bandera está guardada como texto ASCII, el comando `strings` puede filtrarla entre todo el código binario.  Con el comando:

`strings garden.jpg | grep picoCTF`
## **Referencias
https://www.youtube.com/watch?v=xxhnGxgOtWs&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=14