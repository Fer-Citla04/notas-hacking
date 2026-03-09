## **Reto**: JaWT Scratchpad
## **Descripción**
Check the admin scratchpad! http://fickle-tempest.picoctf.net:51827

## **Solución**
- Primero, al entrar a la página del reto y revisar el apartado de las cookies con el "Cookie Editor", encontré una cadena de texto muy larga dividida por dos puntos. Al ver  esto fui a pegarlo en la página de **jwt.io**, me di cuenta de que el valor del usuario era `"citla"` justo el que puse al inicio, pero para avanzar necesitaba que dijera `"admin"`.
- Luego, intenté cambiar el nombre manualmente, pero el sistema me daba un error de firma. Entendí que el token estaba protegido por una contraseña secreta que yo no tenía. Para "romper" esa protección, guardé el código en un archivo y usé una herramienta en mi terminal de Kali llamada **John the Ripper** junto con un diccionario de palabras comunes para que intentara adivinar la clave.

Para encontrar la contraseña y generar el nuevo código, ejecuté estos comandos en mi terminal:

echo `"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoiY2l0bGEifQ.BxMV00bEDEqGZ7-dCdPnanFJeS6aobJKms-NarDSj6Q" > reto.txt`
`john reto.txt --format=HMAC-SHA256 --wordlist=/usr/share/wordlists/rockyou.txt`
`john reto.txt --show`


Después de unos segundos, el sistema encontró la clave: **`ilovepico`**. Con este dato, regresé a la página de **jwt.io**, cambié el usuario a `"admin"`, escribí la clave en el apartado de firma y el sitio me generó un nuevo código válido. Copié ese resultado, lo pegué en mi editor de cookies y, al actualizar la página, por fin apareció la bandera:

```
picoCTF{jawt_was_just_what_you_thought_bbb82bd4a57564aefb32d69dafb60583}
```


## **Referencias
https://www.youtube.com/watch?v=iaKbvrbcSko&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=10