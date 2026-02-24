## **Reto**:  picobrowser
## **Descripción**
This website can be rendered only by picobrowser, go and catch the flag!http://fickle-tempest.picoctf.net:57901
## **Solución**
1. Se accede a la URL y al intentar obtener la bandera, el sitio muestra un mensaje de error indicando: "You're not picobrowser! MOZILLA/5.0...".
2. Se identifica que el servidor utiliza el encabezado **User-Agent** para reconocer qué navegador está realizando la petición. Como se está usando un navegador común (Firefox/Chrome), el servidor bloquea el acceso.
3. Para solucionar esto, se puede interceptar la petición en el apartado de **Red (Network)** de las herramientas de desarrollador, seleccionando la opción de "Editar y volver a enviar" (Edit and Resend).
4. En la sección de encabezados (Headers), se busca la línea de `User-Agent` y se modifica su valor original por la cadena exacta: `picobrowser`.
5. Al enviar la petición modificada, el servidor interpreta que el navegador es el correcto y da la bandera .
```
   picoCTF{p1c0_s3cr3t_ag3nt_fba5c48f}
```

## **Referencias**
https://www.youtube.com/watch?v=9d6-N0oJwOk&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=5