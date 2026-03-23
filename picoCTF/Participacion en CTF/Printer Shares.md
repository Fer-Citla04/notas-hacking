## **Descripción**
Oops! Someone accidentally sent an important file to a network printer—can you retrieve it from the print server? 

Additional details will be available after launching your challenge instance. 
## **Solución**
La resolución se llevó a cabo en tres fases principales utilizando herramientas de **Kali Linux**: 

**1. Reconocimiento de Red** 

Primero, se verificó si el puerto proporcionado estaba activo y aceptaba conexiones. Se utilizó netcat para realizar un escaneo rápido. 

- **Comando:** nc -vz mysterious-sea.picoctf.net 53434 

- **Resultado:** El puerto fue marcado como **open**, confirmando que había un servicio escuchando. 

**2. Enumeración de Recursos Compartidos** 

Dado que el contexto mencionaba impresoras y servidores, se sospechó del protocolo **SMB (Server Message Block)**. Se procedió a listar los recursos compartidos disponibles de forma anónima (Null Session). 

- **Comando:** smbclient -L //mysterious-sea.picoctf.net -p 53434 -N 

- **Hallazgo:** Se identificó un recurso compartido tipo disco llamado **shares** con el comentario _"Public Share With Guests"_. 

**3. Explotación y Extracción** 

Se estableció una conexión directa al recurso identificado para explorar su contenido y descargar la información. 

- **Acceso:** smbclient //mysterious-sea.picoctf.net/shares -p 53434 -N 

- **Exploración:** Dentro del prompt de SMB, se listaron los archivos con ls, encontrando flag.txt. 

- **Descarga:** Se utilizó el comando get flag.txt para traer el archivo a la máquina local. 

- **Lectura:** Finalmente, fuera del cliente SMB, se leyó el archivo: 

- cat flag.txt 


```
 picoCTF{5mb_pr1nter_5h4re5_51f37693} 
```
## **Notas adicionales
- **Vulnerabilidad:** El servidor permitía el acceso a usuarios invitados (Guest) sin necesidad de autenticación, lo cual es una falla de seguridad grave en entornos reales. 
- **Protocolo:** Aunque el puerto 53434 no es el estándar para SMB (usualmente 445), el uso de smbclient con el flag -p permitió interactuar con el servicio sin problemas. 
- **Errores ignorados:** Durante la enumeración, el servidor rechazó conexiones SMB1; esto es normal en sistemas modernos y no afectó la resolución del reto.
