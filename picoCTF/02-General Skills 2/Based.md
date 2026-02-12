## **Reto** : Based -> 1

## **Descripción**
To get truly 1337, you must understand different data encodings, such as hexadecimal or binary. Can you get the flag from this program to prove you are on the way to becoming 1337?

Additional details will be available after launching your challenge instance.

## **Solución**
1. Primero inicializo la instancia y me aparece lo siguiente:
`nc fickle-tempest.picoctf.net 56422`
2. Después me voy a la terminar (en este caso de mismo picoCTF) e inserto el comando anterior y de salida me da:
Fernanda_Floress-picoctf@webshell:~$ nc fickle-tempest.picoctf.net 59670
Let us see how data is stored
socket
Please give the 01110011 01101111 01100011 01101011 01100101 01110100 as a word.
...
you have 45 seconds.....
3. Luego, en cyberchef, pego el código binario que me dio en la terminal y así obtengo la palabra ==socket==.
4. Regreso a la terminal para pegar la palabra que obtuve (solo se tienen 45 segundos para pegar la palabra y que de otra pista).
5. Después la terminal me da 
6. Please give me the  o163 o164 o162 o145 o145 o164 as a word.
y en cyberchef la convierto dandome ==street==.
7. Repito lo anterior y por último la terminal me da Please give me the 6c696d65 as a word. Convirtiendo en cyberchef: ==lime
8. Y así la terminal me da el resultado.

```
 picoCTF{learning_about_converting_values_aeBEA593}
```

## **Referencias**
https://gchq.github.io/CyberChef/