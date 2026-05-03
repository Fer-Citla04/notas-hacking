## **Reto**:  credstuff
## **Descripción**
We found a leak of a blackmarket website's login credentials. Can you find the password of the user `cultiris` and successfully decrypt it?Download the leak [here](https://artifacts.picoctf.net/c/151/leak.tar).The first user in `usernames.txt` corresponds to the first password in `passwords.txt`. The second user corresponds to the second password, and so on.
## **Solución**
1. Este reto establece una correspondencia directa uno a uno entre las líneas de ambos archivos de texto. Para localizar la credencial específica, abrimos el archivo usernames.txt y utilizamos la función de búsqueda de un editor de texto para encontrar al usuario cultiris, identificando que se encuentra en la línea 378.
2. Luego nos dirigimos al archivo passwords.txt y extrajimos el contenido de la misma línea (378), obteniendo la siguiente cadena cifrada: `cvpbPGS{P7e1S_54I35_71Z3}`
3. El texto estaba protegido por un Cifrado ROT13. Para decodificar la bandera, ejecutamos el siguiente comando en la terminal utilizando el traductor de caracteres `tr`:

`echo -n cvpbPGS{P7e1S_54I35_71Z3} | tr "A-Za-z" "N-ZA-Mn-za-m"`

```
picoCTF{C7r1F_54V35_71M3}
```
## **Notas adicionales
- **Cifrado ROT13**: una variante del cifrado César que desplaza el alfabeto 13 posiciones.