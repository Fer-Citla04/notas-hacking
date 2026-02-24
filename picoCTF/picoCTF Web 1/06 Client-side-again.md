## **Reto**: - Client-side-again
## **Descripción**
Can you break into this super secure portal?http://fickle-tempest.picoctf.net:56446
## **Solución**
1. Se accede a la URL y se observa que el código de validación está ofuscado. Para entender la lógica, se procesa el script en **JS Nice**, lo que permite identificar un arreglo de cadenas llamado `_0x5a46` y una función de rotación que reordena sus elementos.
2. Al analizar el código limpio, se encuentra la función `verify()`, la cual utiliza subcadenas y una función auxiliar `_0x4b5b` para extraer valores del arreglo y compararlos con la contraseña ingresada.
3. Para reconstruir la bandera, se sigue el orden de las comparaciones `if` en el código desofuscado:
- `substring(0, 8)` comparado con `_0x4b5b("0x3")`: **picoCTF{**
- `substring(8, 16)` comparado con `_0x4b5b("0x4")`: **not_this**
- `substring(16, 24)` comparado con `_0x4b5b("0x6")`: **_again_4**
- `substring(24, 32)` comparado con `_0x4b5b("0x5")`: **daf93}**

4. Así es como se encontró la bandera

```
picoCTF{not_this_again_4daf93}
```

## **Referencias**
https://www.youtube.com/watch?v=rsPT722MkzQ&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=6