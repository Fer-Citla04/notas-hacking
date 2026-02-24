## **Reto**: where are the robots

## **Descripción**
Can you find the robots?http://fickle-tempest.picoctf.net:60912

Pista: What part of the website could tell you where the creator doesn't want you to look?
## **Solución**
1. Se accede a la URL y se observa un sitio web con nula interactividad. Tras revisar el código fuente HTML, no se encuentra nada referente a la bandera.
2. Luego, basado en el nombre del reto, se investiga la existencia del archivo **`robots.txt.
3. Se accede manualmente a dicho archivo ingresando a la ruta: `http://fickle-tempest.picoctf.net:60912/robots.txt`.
4. Al visualizar el contenido, se identifica una instrucción `Disallow` que apunta a una página que no estaba enlazada en el HTML original: `/cc6b1.htm`.
5. Se ingresa esa ruta en el URL del navegador.
6. En esta página oculta se localiza la bandera

```
picoCTF{ca1cu1at1ng_Mach1n3s_cc6b1}
```

## **Referencias**
https://www.youtube.com/watch?v=LRgg3Kcnbuw&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=2