## **Reto**: - dont-use-client-side
## **Descripción**
Can you break into this super secure portal?http://fickle-tempest.picoctf.net:64930
## **Solución**
1. Se accede a la URL y se intenta ingresar una contraseña cualquiera para probar el sistema. Al dar clic en "verify", aparece un mensaje de "Incorrect password".
2. Al revisar el código fuente de la página, se identifica que la validación de la contraseña ocurre completamente en el navegador (lado del cliente) mediante una función de JavaScript llamada `verify()`.
3. Al analizar el script, se observa que la contraseña se divide en fragmentos de 4 caracteres (determinados por la variable `split = 4`) y se comparan mediante subcadenas (`substring`).
4. Para obtener la bandera, se deben ordenar los fragmentos según la posición que indica el código:
- `substring(0, split)`: **pico**
- `substring(split, split*2)`: **CTF{**
- `substring(split*2, split*3)`: **no_c**
- `substring(split*3, split*4)`: **lien**
- `substring(split*4, split*5)`: **ts_p**
- `substring(split*5, split*6)`: **lz_2
- `substring(split*6, split*7)`: **eb02**
- `substring(split*7, split*8)`: **b45}**

1. Al unir todos los fragmentos en orden, se obtiene la contraseña y por lo tanto también la bandera.


```
   picoCTF{no_clients_plz_2eb02b45}
```

## **Notas adicionales**
- **Client-side:** Se refiere a todo lo que ocurre directamente en el navegador del usuario. En este reto, el error es que la contraseña es visible para cualquiera que sepa ver el código fuente.
- **Función substring():** Es un método de JavaScript que extrae caracteres desde un índice hasta otro. Por ejemplo, `(split*2, split*3)` significa extraer del carácter 8 al 12.
## **Referencias**
https://www.youtube.com/watch?v=19Hkmb1Guzk&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=4