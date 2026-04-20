## **Reto**:  la cifra de
## **Descripción**
I found this cipher in an old book.Can you figure out what it says? Connect with nc fickle-tempest.picoctf.net 64937.
## **Solución**
1. Me conecté al servidor proporcionado . Utilicé la terminal de Linux con el siguiente comando: `nc fickle-tempest.picoctf.net 64937`
2. Al recibir el texto, noté que era un bloque extenso de caracteres que mantenía una estructura gramatical pero el contenido era ilegible.
3. Debido a la pista del título "la cifra de". Entonces utilicé una herramienta de identificación de cifrados (**dCode.fr**).
4. La herramienta identificó el texto como un Cifrado de Vigenère. Al intentar descifrarlo, la herramienta sugirió que la clave podría ser "FLAG". Sin embargo, al aplicarla a todo el texto, el resultado era inconsistente.
5. La clave no era estática, sino que rotaba en ciertas secciones del documento. Utilizando la robustez de la herramienta para realizar un análisis de frecuencia y fuerza bruta sobre la clave, logré estabilizar el texto.

Por último, entre los párrafos decodificados: 

It is interesting how in history people often receive credit for things they did not create

During the course of history, the Vigenère Cipher has been reinvented many times

It was falsely attributed to Blaise de Vigenère as it was originally described in 1553 by Giovan Battista Bellaso in his book La cifra del. Sig. Giovan Battista Bellaso 

For the implementation of this cipher a table is formed by sliding the lower half of an ordinary alphabet for an apparently random number of places with respect to the upper halfpicoCTF{b311a50_0r_v1gn3r3_c1ph3rdbdC91a3}

The first well-documented description of a polyalphabetic cipher however, was made around 1467 by Leon Battista Alberti.

The Vigenère Cipher is therefore sometimes called the Alberti Disc or Alberti Cipher.

In 1508, Johannes Trithemius invented the so-called tabula recta (a matrix of shifted alphabets) that would later be a critical component of the Vigenère Cipher.

Bellaso’s second booklet appeared in 1555 as a continuation of the first. The lower halves of the alphabets are now shifted regularly, but the alphabets and the index letters are mixed by means of a mnemonic key phrase, which can be different with each correspondent.

Encontré la bandera 
```
picoCTF{b311a50_0r_v1gn3r3_c1ph3rdbdC91a3}
```
## **Referencias
https://www.guballa.de/vigenere-solver
https://www.dcode.fr/vigenere-cipher