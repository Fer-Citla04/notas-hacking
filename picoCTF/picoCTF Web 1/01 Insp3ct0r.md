## **Reto**: Insp3ct0r

## **Descripción**
Kishor Balan tipped us off that the following code may need inspection:http://fickle-tempest.picoctf.net:56408

## **Solución**
1. Lo primero fue ir al link que da en la misma descripción.
2. Luego dar clic derecho para entrar al código fuente de la página.
3. En ese código viene la primera parte de la bandera
   `<!-- Html is neat. Anyways have 1/3 of the flag: picoCTF{tru3_d3 -->`
4. Como la pista dice que hay tres partes, procedemos a encontrar las otras dos.
5. Accedemos a la parte href="[mycss.css](http://fickle-tempest.picoctf.net:56408/mycss.css)"> del código y al entrar, también en comentarios, nos dan la segunda parte de la bandera `/* You need CSS to make pretty pages. Here's part 2/3 of the flag: t3ct1ve_0r_ju5t */`
6. Por último, ingresamos la parte src="[myjs.js](http://fickle-tempest.picoctf.net:56408/myjs.js)" del código y dentro en comentarios viene la parte tres de la bandera `lucky?302945a7}`
7. Así es como se encuentra la bandera de este reto.
```
picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?302945a7}
```

## **Referencias**
https://www.youtube.com/watch?v=f1infpFomIM&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=1