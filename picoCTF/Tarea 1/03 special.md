## **Reto**: special

## **Descripción**
Don't power users get tired of making spelling mistakes in the shell? Not anymore! Enter Special, the Spell Checked Interface for Affecting Linux. Now, every word is properly spelled and capitalized... automatically and behind-the-scenes! Be the first to test Special in beta, and feel free to tell us all about how Special streamlines every development process that you face. When your co-workers see your amazing shell interface, just tell them: That's Special (TM) Start your instance to see connection details. `ssh -p 64157 ctf-player@saturn.picoctf.net` The password is `fd7746b4`
## **Solución**
1. Primero, Me conecté por SSH y me encontré con un shell que me corregía todo lo que escribía. Si ponía `ls`, me lo cambiaba a `Is`  y  decía que no encontraba el comando.
2. Intenté con muchos comandos que han ayudado a las soluciones de retos anteriores, también probé con `$ls`, `*ls`, poniendo comillas `"ls"` y hasta con barras `\ls`, pero siempre se agregaba letras como `Als` o `Also`.
3. Debido a esto investigué y encontré una página con comandos especiales de Bash que usan llaves `{}`.
4. Luego, probé esos comandos e inicié con `${parameter=ls}` y  mostró una carpeta llamada `blargh`.
5. Con el comando `${parameter=ls blargh}` sirvió para ver qué había dentro de la carpeta.
6. Dentro estaba el archivo `flag.txt`. 
7. Para leer el archivo, lo hice con el comando `${parameter=cat < blargh/flag.txt}`
8. Y así fue como se encontró la bandera de este reto

```
picoCTF{5p311ch3ck_15_7h3_w0r57_f578af59}
```

## **Notas adicionales**
- **`ls` / `Ls`**: Son los comandos para listar archivos. Aquí fallaron porque shell los cambiaba a `Is`, y como en Linux las mayúsculas importan, el sistema no los reconocía.
- **`$ls` / `*ls` / `\ls` / `"ls"`**: Estos fueron los primeros intentos para "romper" el autocorrector. El `$` intenta llamar una variable, el `*` es un comodín, la `\` es para escapar caracteres y las `""` son para texto literal. En este reto no sirvieron porque  shell estaba programada para meterles una "A" o una "O" al principio 
- **`${parameter=ls}`**: En Bash, esto le dice al sistema: "Si la variable _parameter_ no existe, asígnale el valor _ls_". Al hacerlo dentro de las llaves, el comando se procesa de una forma que el autocorrector no puede detectar ni cambiar la primera letra.
- **`${parameter=cat < blargh/flag.txt}`**: Eso sirve para decirle al comando `cat` que tome el contenido de `flag.txt` y lo muestre en la pantalla. 
## **Referencias**
https://josephkimiri.github.io/posts/Special/