## **Reto**:  Scavenger Hunt
## **Descripción**
There is some interesting information hidden around this site. Can you find it? http://wily-courier.picoctf.net:62359/
## **Solución**
1. Se accede al link que nos dan en la descripción y se inspecciona el código fuente HTML. En los comentarios del archivo principal, se localiza la primera parte de la bandera: `picoCTF{th4ts_4_l0t_0f_`.
2. Luego, se revisa el archivo de estilos CSS `mycss.css`. En los comentarios, se encuentra la segunda parte: `h3rd3r_8_7d6`.
3. Se inspecciona el archivo Java `myjs.js`. Aunque no contiene un fragmento de la bandera,  si da una pista sobre cómo evitar que Google indexe el sitio, lo que sugiere investigar el archivo **`robots.txt`**.
4. Al navegar a http://wily-courier.picoctf.net:62359/robots.txt, se encuentra la tercera parte de la bandera: `j5_ar3_c00l_` junto con otra pista que menciona que el servidor es Apache.
5. Se intenta acceder al archivo de configuración de directorios **`.htaccess`**. Al navegar a `http://wily-courier.picoctf.net:62359/.htaccess`, se revela la cuarta parte: `423712b8}`.
6. La última pista menciona el uso de computadoras **Mac**. Esto sugiere buscar el archivo oculto de metadatos de macOS llamado **`.DS_Store`**.
7. Al acceder a http://wily-courier.picoctf.net:62359/.DS_Store, se obtiene la última parte de la bandera.


```
picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_9588550}
```

## **Notas adicionales
- **`robots.txt`**: Es un archivo de texto plano que indica a los bots de los buscadores qué páginas o archivos no deben solicitar. 
- **`.htaccess` (Hypertext Access)**: Es un archivo de configuración utilizado por servidores web **Apache**. Permite definir reglas de acceso, redirecciones y seguridad a nivel de directorio. 
- **`.DS_Store` (Desktop Services Store)**: Es un archivo oculto creado automáticamente por el sistema operativo **macOS** (Finder) en cada carpeta. Almacena metadatos sobre la visualización de iconos y fondos. 
## **Referencias
https://www.youtube.com/watch?v=E2gN3AGHirc&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=13


