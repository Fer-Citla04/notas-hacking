## **Reto**:  Tapping
## **Descripción**
Theres tapping coming in from the wires.

What's it saying nc fickle-tempest.picoctf.net 59218.
## **Solución**
1. Utilicé la terminal para conectarme al servidor remoto y recibir el flujo de información. Al ejecutar el comando: `nc fickle-tempest.picoctf.net 59218`
2. Obtuve como respuesta una cadena compuesta únicamente por puntos, guiones y espacios, además de llaves que delimitaban el contenido. El mensaje recibido fue: 
┌──(kali㉿kali)-[~/Documentos/Tapping]
└─$ nc fickle-tempest.picoctf.net 59218 
.--. .. -.-. --- -.-. - ..-. { -- ----- .-. ... ...-- -.-. ----- -.. ...-- .---- ... ..-. ..- -. -.-. ----. .---- ..-. -.... ..--- ----- -.... } 
 
 3. Debido a la estructura de puntos y rayas, identifiqué inmediatamente que se trataba de Código Morse.
 4. Utilice CyberChef; seleccioné la operación "From Morse Code".

```
PICOCTF{M0RS3C0D31SFUNC91F6206} 
```

## **Referencias
https://gchq.github.io/CyberChef/#recipe=From_Morse_Code('Space','Line%20feed')&input=Li0tLiAuLiAtLi0uIC0tLSAtLi0uIC0gLi4tLiB7IC0tIC0tLS0tIC4tLiAuLi4gLi4uLS0gLS4tLiAtLS0tLSAtLi4gLi4uLS0gLi0tLS0gLi4uIC4uLS4gLi4tIC0uIC0uLS4gLS0tLS4gLi0tLS0gLi4tLiAtLi4uLiAuLi0tLSAtLS0tLSAtLi4uLiB9IA0K&ieol=CRLF