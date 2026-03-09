## **Reto**:  Irish-Name-Repo 1
## **Descripción**
Do you think you can log us in? Try to see if you can login! http://fickle-tempest.picoctf.net:53842.

## **Solución**
1. Lo primero entrar a la pagina que se nos dió.
2. Después, se accedió a la pantalla de login y se inspeccionó el código fuente, donde se identificó un campo oculto llamado `debug` establecido en el valor "0".
3. Se utilizó el inspector del navegador para cambiar el valor de `debug` a "1".
4. Al observar que la consulta concatenaba directamente las entradas del usuario (`SELECT * FROM users WHERE name='...' AND password='...'`), se identificó que el sistema era vulnerable a la manipulación de la lógica SQL.
5. Luego, se investigó una inyección básica utilizando el operador lógico **OR** acompañado de una sentencia siempre verdadera (`' OR 1=1;`) para invalidar el resto de la condición de la contraseña.
6. Se ingresó esta inyección en el campo de la contraseña.
7. Y al enviarlo, el sistema permitió el acceso y entregó la bandera.

```
picoCTF{s0m3_SQL_85832275}
```

## **Referencias
https://www.youtube.com/watch?v=0EDbUSDqrng&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=7