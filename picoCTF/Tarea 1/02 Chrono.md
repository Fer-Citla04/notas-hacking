## **Reto**: chrono

## **Descripción**
How to automate tasks to run at intervals on linux servers? Use ssh to connect to this server:

`Server: saturn.picoctf.net`
`Port: 57651`
`Username: picoplayer` 
`Password: ENAFb6zfzn`

## **Solución**
1. Primero, nos conectamos al servidor mediante SSH con el puerto y la contraseña indicados: `ssh -p 52361 picoplayer@saturn.picoctf.net`
2. Una vez dentro, navegamos hacia atrás en los directorios para explorar la raíz del sistema: `cd ..` `cd ..`
3. Listamos los archivos en la raíz (`/`) con el comando `ls` para ver qué directorios hay disponibles. Intentamos entrar a la carpeta `/challenge`, pero el sistema nos deniega el acceso: `cd challenge/`
4. Como el reto menciona tareas programadas en intervalos, se revisó el archivo de configuración de cron del sistema, que es donde se gestionan estas tareas en Linux: `cat /etc/crontab`
5. Al leer el archivo, se encontró la bandera comentada directamente en las primeras líneas del archivo: `picoCTF{Sch3DUL7NG_T45K3_L1NUX_1d781160}`

## **Notas adicionales**
- **/etc/crontab**: Es el archivo donde se definen las tareas que el sistema debe ejecutar automáticamente en periodos de tiempo determinados.
- **cat**: Es el comando utilizado para mostrar el contenido de archivos de texto directamente en la terminal sin necesidad de abrirlos en un editor.
