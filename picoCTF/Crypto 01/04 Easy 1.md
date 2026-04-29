## **Reto**:  Easy 1
## **Descripción**
The one time pad can be cryptographically secure, but not when you know the key. Can you solve this?We've given you the encrypted flag, key, and a table to help UFJKXQZQUNB with the key of SOLVECRYPTO. Can you use this [table](https://challenge-files.picoctf.net/c_fickle_tempest/859ffc313a4d8b63149f144745043a7312fc4f993e405eeeb8ee5ae6ca8444a8/table.txt) to solve it?.
## **Solución**
1. A diferencia del cifrado César, el cifrado que se necesitaba (Vigenère) es un cifrado polialfabético donde cada letra de la clave determina el desplazamiento de la letra correspondiente en el mensaje. 
2. Luego, al contar con la clave completa, el proceso consiste en alinear el texto cifrado con la clave y realizar una sustracción para cada par de caracteres. La lógica  aplicada para cada letra es la siguiente:

`P = (C - K) (mod26)`

Donde P es el texto plano, C es el carácter cifrado y K es el carácter de la clave 

3. Teniendo en cuenta lo anterior, realicé la alineación de los caracteres para verificar los primeros resultados:

- **U (20) - S (18) = 2 (C)**

- **F (5) - O (14) = -9 $\equiv$ 17 (R)**

- **J (9) - L (11) = -2 $\equiv$ 24 (Y)**

4. Para completar el proceso, utilicé CyberChef aplicando _Vigenère Decode_ con la clave proporcionada.
5. Por último, el resultado reveló la bandera

```
picoCTF{CRYPTOISFUN}
```
## **Notas adicionales
- Aritmética Modular:** En criptografía, el uso de $\pmod{26}$ permite que los resultados negativos "den la vuelta" al alfabeto, manteniendo siempre el flujo dentro de los caracteres A-Z.
## **Referencias
https://gchq.github.io/CyberChef/