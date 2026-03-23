## **Reto**:  Operation Oni.
## **Descripción**
Download this disk image, find the key and log into the remote machine.

Note: if you are using the webshell, download and extract the disk image into /tmp not your home directory.

Download disk image

Remote machine: ssh -i key_file -p 52900 ctf-player@saturn.picoctf.net
## **Solución**
1. Descargué la imagen con `wget` y la descomprimí usando `gunzip disk.flag.img.gz`.
2. Usé `mmls disk.flag.img` para identificar las particiones. Encontré tres particiones, dos de ellas de tipo **Linux (0x83)**.
3. Analicé ambas particiones con `fsstat` para verificar cuál contenía el sistema de archivos del usuario.
4. Utilicé `fls -o [offset] disk.flag.img` para navegar por las particiones.
5. Busqué específicamente la carpeta personal del usuario, que suele estar en `/home/ctf-player/` o en el directorio `/root/`.
6. Dentro del directorio del usuario, busqué la carpeta oculta **`.ssh/`**. Esta carpeta es estándar en Linux para guardar llaves de acceso.
7. Dentro de `.ssh/`, identifiqué el archivo de la llave privada (comúnmente llamado `id_rsa`).
8. Usé el comando `icat` para extraer el contenido del inodo de la llave y guardarlo en mi máquina local: `icat -o [offset] disk.flag.img [inodo_de_la_llave] > key_file`
9. SSH tiene una regla de seguridad estricta: si la llave privada tiene permisos que permitan que otros usuarios la lean, el cliente SSH la rechazará por ser "insura".
10. Verifiqué con `ls -l key_file` y vi que los permisos eran demasiado abiertos.
11. Corregí los permisos para que solo yo (el dueño) pudiera leerla: `chmod 600 key_file`
12. Finalmente, realicé la conexión SSH indicando el archivo de identidad extraído: `ssh -i key_file -p 52900 ctf-player@saturn.picoctf.net`
13. Una vez dentro del servidor remoto, listé los archivos con `ls` y encontré el archivo `flag.txt` con la bandera.
```
picoCTF{k3y_5l3u7h_af277f77}
```

## **Notas adicionales
- chmod 600:** Este comando es vital al trabajar con llaves privadas. Significa que el dueño tiene permisos de lectura y escritura (`6`), mientras que el grupo y otros no tienen ningún permiso (`00`).
- **id_rsa:** Es el nombre por defecto que genera la herramienta `ssh-keygen` para la llave privada de un usuario.
## **Referencias