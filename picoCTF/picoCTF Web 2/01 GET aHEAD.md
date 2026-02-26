## **Reto**: GET aHEAD
## **Descripción**
Find the flag being held on this server to get ahead of the competition http://wily-courier.picoctf.net:55806/
## **Solución**
1. Se accede a la liga de la descripción, y al entrar se visualiza una página con dos botones que permiten cambiar el color de fondo a rojo o azul. 
2.  Después, se abre el Inspector del Navegador y se navega a la pestaña de Red (Network). Se realiza una acción en la página (clic en un botón) para capturar una solicitud inicial.
3. Se selecciona la solicitud capturada y se utiliza la opción de Editar y volver a enviar.
4. En la configuración de la nueva petición, se modifica el método de GETpor el método **HEAD**.
5. Al enviar esta solicitud modificada, se revisa la respuesta y  la bandera se encuentra almacenada directamente en esta sección.
```
picoCTF{r3j3ct_th3_du4l1ty_8b13f07}
```
## **Notas adicionales**
Existen otras formas de resolver este reto:

**Uso de la Consola :** Se puede obtener la bandera directamente desde la terminal utilizando el comando `curl -I [URL]`. El parámetro `-I` indica a curl que realice una petición de tipo **HEAD**, devolviendo únicamente los encabezados donde reside la bandera.

**Uso de Burp Suite:** Este software funciona como un **Proxy** que intercepta la comunicación entre el navegador y el servidor. Permite detener la petición (Intercept on), cambiar el verbo GET por HEAD manualmente en el editor de texto y observar la respuesta en el historial HTTP.

 **Método HEAD:** Es un verbo HTTP diseñado para obtener la misma información que un GET (metadatos, tipo de archivo, tamaño), pero sin descargar el contenido real del sitio. Es muy útil para verificar la existencia de un recurso sin consumir ancho de banda.
 
 **FoxyProxy:** Es una extensión recomendada para gestionar el uso de proxies como Burp Suite, permitiendo activar o desactivar la redirección del tráfico con un solo clic.

## **Referencias**
https://www.youtube.com/watch?v=oiZk0tIkR48&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=11