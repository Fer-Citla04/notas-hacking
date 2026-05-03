## **Reto**:  substitution0
## **Descripción**
A message has come in but it seems to be all scrambled. Luckily it seems to have the key at the beginning. Can you crack this substitution cipher?Download the message [here](https://artifacts.picoctf.net/c/152/message.txt).
## **Solución**
1. Descargamos el archivo de la descripción con wget 
2. Al ejecutar el comando `cat message.txt`, identificamos dos elementos fundamentales para la resolución: una **clave (Key)** compuesta por una cadena de 26 letras (`DECKFMYIQJRWTZPXGNABUSOLVH`) y un texto cifrado que corresponde a un extracto literario con las letras intercambiadas, finalizando con la bandera cifrada: `xqcpCBM{5UE5717U710Z_3S0WU710Z_59533D2F}`.
3. Para la ejecución del descifrado se hizo en**Boxentriq** . Ingresamos el texto cifrado y configuramos la clave para realizar la sustitución inversa, lo que permitió recuperar el texto original en inglés.

```
picoCTF{5UB5717U710N_3V0LU710N_59533A2E}
```
## **Referencias**
https://www.boxentriq.com/ciphers/keyed-caesar-cipher
