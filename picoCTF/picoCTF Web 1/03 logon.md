## **Reto**: logon
## **Descripción**
The factory is hiding things from all of its users.Can you login as Joe and find what they've been looking at? http://fickle-tempest.picoctf.net:55046

Pista: Hmm it doesn't seem to check anyone's password, except for Joe's?
## **Solución**
1.  Se accede a la URL y se intenta iniciar sesión con el usuario `Joe`.El sistema rechaza cualquier contraseña incorrecta. Al probar con un nombre de usuario cualquiera, en mi caso admin y cualquier contraseña, el sistema permite el ingreso, no permite ver la bandera.
2. Para manipular los datos, se instaló una extensión **"Cookie Editor"**.Esta herramienta permite visualizar y modificar datos que el servidor almacena.
3. Se inició sesión nuevamente y al abrir la extensión  se identifican tres cookies: `username`, `password` y `admin`.
4. Al ingresar a la cookie `admin`, nos damos cuenta que tiene el valor `False`. Entonces, procedemos a editar este valor, cambiándolo a `True` y guardando los cambios.
5. Se refresca la página y así nos da la bandera.
```
   picoCTF{th3_c0nsp1r4cy_l1v3s_4d184b0d}
```
## **Notas adicionales
También es posible obtener el resultado enviando los encabezados modificados directamente desde la consola:
 `curl -s -H "Cookie: admin=True" http://fickle-tempest.picoctf.net:55046/flag | grep pico`

## **Referencias**
https://www.youtube.com/watch?v=P2njyHWhu1U&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=3