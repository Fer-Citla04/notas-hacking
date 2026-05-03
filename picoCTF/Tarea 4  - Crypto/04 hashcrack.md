## **Reto**:  hashcrack
## **Descripción**
A company stored a secret message on a server which got breached due to the admin using weakly hashed passwords. Can you gain access to the secret stored within the server?Access the server using `nc verbal-sleep.picoctf.net 61810`
## **Solución**

1. Me conecté al servidor de la descripcion con el comando nc verbal-sleep.picoctf.net 61810
2. Apareció lo siguiente: 
   Welcome!! Looking For the Secret?
   We have identified a hash: 482c811da5d5b4bc6d497ffa98491e38
3. Entré a la página crackstation.net
![[Pasted image 20260503143313.png]]

![[Pasted image 20260503143407.png]]

![[Pasted image 20260503143454.png]]


4. Y al final me devolvió la bandera
```
picoCTF{UseStr0nG_h@shEs_&PaSswDs!_93e052d7}
```
## **Referencias**
https://crackstation.net/