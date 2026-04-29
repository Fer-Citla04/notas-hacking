## **Reto**:  Caesar
## **Descripción**
Decrypt this message.Message: [message](https://challenge-files.picoctf.net/c_fickle_tempest/e1502af9ec6ede316e796b88ed49d0ed1be4e7724511e3e96a2f42e6af597f01/data.enc)
## **Solución**
1. Utilicé el comando `ls` para localizar el archivo y `file data.enc` para confirmar que se trataba de un archivo de un ASCII y no un binario. 
2. Al ejecutar `cat data.enc`, visualicé el mensaje cifrado: `picoCTF{hwtxxnslymjwzgnhtswlvhsgdv}`. Pero al ponerlo como respuesta, dió incorrecto.
3. Para resolverlo de manera eficiente desde la terminal de Linux, seleccioné el comando `tr` , el cual es ideal para realizar sustituciones de caracteres de forma masiva.
4. Teniendo en cuenta lo anterior, ejecuté el siguiente comando:

`cat data.enc | tr 'a-zA-Z' 'v-za-uV-ZA-U'`

Este comando movió cada letra 5 posiciones hacia atrás en el alfabeto.

```
picoCTF{crossingtherubiconrgqcnbyq}
```
## **Notas adicionales
- **Comando tr:** Es una herramienta extremadamente potente en sistemas Unix para la manipulación de flujos de texto. Permite mapear un set de caracteres a otro de forma instantánea.
- **Sustitución Alfabética:** El comando `tr 'a-z' 'v-za-u'` funciona definiendo el inicio del alfabeto en la letra 'v', lo que desplaza efectivamente el abecedario original.

