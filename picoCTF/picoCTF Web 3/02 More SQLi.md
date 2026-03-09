## **Reto**: More SQLi
## **Descripción**
Can you find the flag on this website.Try to find the flag here.
## **Solución**
- Lo primero que se hizo fue entrar a la página.
- Se aplicó una inyección SQL básica en los campos de credenciales: `' OR 1=1; --`.
- Una vez dentro, se identificó que la tabla mostrada tenía tres columnas, por lo que se utilizó el comando `UNION SELECT 1, 2, 3` para confirmar el número de columnas necesarias para la inyección.
- Después, se realizó una consulta al esquema de la base de datos mediante `UNION SELECT 1, sql, 3 FROM sqlite_master` para obtener la estructura de todas las tablas existentes.
- Gracias a esta consulta, se identificó una tabla con el nombre sugerente de `more_table` la cual contenía una columna denominada `flag`.
- Por último, se ejecutó la sentencia final: `UNION SELECT 1, flag, 3 FROM more_table` para extraer el contenido de esa columna y visualizar la bandera.

```
	picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_e3e46aae}
```
## **Referencias
https://www.youtube.com/watch?v=clMe4yqL6yU&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=63