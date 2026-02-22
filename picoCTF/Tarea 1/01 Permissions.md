## **Reto**: Permissions

## **Descripción**
Can you read files in the root file? The system admin has provisioned an account for you on the main server: `ssh -p 54265 picoplayer@saturn.picoctf.net` Password: `33qE7mB5BF` Can you login and read the root file?
## **Solución**
1. Primero, me conecté al servidor mediante SSH con el puerto y contraseña que nos proporcionaron en la decripción del reto `ssh -p 54265 picoplayer@saturn.picoctf.net`
   
2. Una vez dentro, vi las carpetas que había. Al ver que la carpeta personal está vacía, fui al directorio raíz con `cd /` y listé los archivos. 
   En el directorio raíz con ls vi que había varios archivos 
   picoplayer@challenge:/$ ls
`bin   challenge  etc   lib    lib64   media  opt   root  sbin  sys  usr`
`boot  dev        home  lib32  libx32  mnt    proc  run   srv   tmp `
 Al que tenemos que entrar es a challenge.
 
 3. Al poner el comando cd challange/ no permitia entrar a la carpeta, pues no tenía los permisos. Entonces revisé los privilegios de superusuario para ver si hay alguna brecha de seguridad: `sudo -l`. A lo que el sistema nos indica que podemos ejecutar el editor de texto **vi** como root: `(ALL) /usr/bin/vi`

 4. Teniendo en cuenta lo anterior entré al editor con privilegios elevados: `sudo vi`. Una vez adentro, agregué `:!/bin/bash` y presioné **Enter**.
 5. Ahora, como el prompt cambió a `root@challenge`, sabemos que tenemos acceso total. Y así ya me pude dirigir a la carpeta del administrador`cd /root`

 6. Al usar `ls` no aparece nada, por lo que usamos `ls -la` para ver archivos ocultos. Ahí encontramos el archivo `.flag.txt`.

 7. Por último, leemos el archivo para obtener la bandera: `cat .flag.txt` a lo que así me dio la bandera de este reto.
```
picoCTF{uS1ng_v1m_3dit0r_3dd6dcf4}
```
## **Notas adicionales**
- **sudo -l**: Es un comando que lista los privilegios permitidos para nuestro usuario. En este caso, nos permitió ver que `vi` era nuestra vía de escape.
- **ls -la**: Se utiliza para listar todos los archivos, incluyendo los "ocultos" (aquellos que empiezan con un punto).
- **:!/bin/bash**: Es una función de `vi` que permite ejecutar comandos de sistema. Al ejecutarlo bajo `sudo`, nos otorga una shell con privilegios de root.

## **Referencias**
https://medium.com/@petemuiruri/permissions-writeup-picoctf-2023-be95c95f80a5