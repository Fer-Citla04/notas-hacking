## **Reto**:   CanYouSee
## **Descripción**
How about some hide and seek?Download this file [here](https://artifacts.picoctf.net/c_titan/4/unknown.zip).
## **Solución**
1. Utilicé la herramienta **Aperi Solve** para realizar un escaneo automático de la imagen. La herramienta detectó que la imagen contenía datos ocultos mediante **Steghide** 
2. Al no tener extensión, utilicé el comando `file` que lo identificó como **ASCII text**. Al renombrarlo a `.txt`, encontré el mensaje: _"La bandera no está aquí; quizás deberíamos pensar en términos más sencillos. Datos que explican datos."_
3. Regresé a inspeccionar los metadatos de la imagen original y encontré `cGljb0NURntNRTc0RDQ3QV9ISUREM05fZDhjMzgxZmR9Cg==`
4.  Utilicé **CyberChef**  para procesar la cadena.
cGljb0NURntNRTc0RDQ3QV9ISUREM05fZGVjYTA2ZmJ9Cg==

 La cadena se tradujo directamente al formato de la bandera.
```
picoCTF{ME74D47A_HIDD3N_deca06fb}
```

## **Referencias
https://cyberchef.org/