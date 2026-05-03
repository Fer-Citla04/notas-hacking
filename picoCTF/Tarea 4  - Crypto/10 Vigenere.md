## **Reto**:  Vigenere
## **Descripción**
Can you decrypt this message?Decrypt this [message](https://artifacts.picoctf.net/c/160/cipher.txt) using this key "CYLAB".
## **Solución**
1. Descargué el archivo de la descripción con `wget`.
2. Ejecuté el cypher.txt con cat y apareció lo siguiente
   ┌──(kali㉿kali)-[~/Documentos/Vigenere]
└─$ cat cipher.txt 
rgnoDVD{O0NU_WQ3_G1G3O3T3_A1AH3S_2951c89f}

3. Fui a cyberchef y pegue el texto de la siguiente manera
   ![[Pasted image 20260503163436.png]]

4. Y así conseguí la bandera del reto.
```
picoCTF{D0NT_US3_V1G3N3R3_C1PH3R_2951a89h}
```
## **Referencias**
https://gchq.github.io/CyberChef/#recipe=Vigen%C3%A8re_Decode('CYLAB')&input=cmdub0RWRHtPME5VX1dRM19HMUczTzNUM19BMUFIM1NfMjk1MWM4OWZ9