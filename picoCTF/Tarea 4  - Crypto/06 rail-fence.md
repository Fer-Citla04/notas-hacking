## **Reto**:  rail-fence
## **Descripción**
A type of transposition cipher is the rail fence cipher, which is described [here](https://en.wikipedia.org/wiki/Rail_fence_cipher). Here is one such cipher encrypted using the rail fence with 4 rails. Can you decrypt it?Download the message [here](https://artifacts.picoctf.net/c/189/message.txt).Put the decoded message in the picoCTF flag format, `picoCTF{decoded_message}`.
## **Solución**
1. Descargamos el archivo de la descripción de  `wget` 
2. Al ejecutar el comando `cat message.txt`, visualizamos el siguiente texto cifrado: `Ta _7N6D8Dhlg:W3D_H3C31N__387ef sHR053F38N43DFD i33___N6`
3. Después se procedió a la identificación del cifrado basándonos en la descripción del reto, que especifica el uso de un **Rail Fence Cipher**.
4. Para la lógica del descifrado, aplicamos el proceso inverso de transposición:

- **Construcción de la rejilla**: Se preparó una matriz con 4 filas y una longitud equivalente al número total de caracteres del mensaje cifrado.
- **Marcado del zigzag**: Se trazó el camino en forma de "W" a través de los rieles para determinar la posición exacta de cada letra.
- **Llenado y lectura**: Se colocaron los caracteres del archivo horizontalmente en las posiciones marcadas y, finalmente, se leyó el mensaje siguiendo el patrón de zigzag (de arriba hacia abajo y viceversa).

1. El mensaje se reordenó correctamente revelando la siguiente frase: `The flag is: WH3R3_D035_7H3_F3NC3_8361N_4ND_3ND_83F6D8D7`

```
picoCTF{WH3R3_D035_7H3_F3NC3_8361N_4ND_3ND_83F6D8D7}
```
## **Referencias**
https://www.dcode.fr/rail-fence-cipher