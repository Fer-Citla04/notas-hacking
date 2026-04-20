## **Reto**:  Secret of the Polyglot
## **Descripción**
The Network Operations Center (NOC) of your local institution picked up a suspicious file, they're getting conflicting information on what type of file it is. They've brought you in as an external expert to examine the file. Can you extract all the information from this strange file?Download the suspicious file [here](https://artifacts.picoctf.net/c_titan/8/flag2of2-final.pdf).
## **Solución**
1. Primero, abrí el archivo PDF proporcionado. A simple vista, el documento contenía texto que parecía ser la segunda mitad de una bandera: `1n_pn9_&_pdf_249d05c0}`. Sin embargo, la primera parte no era visible en el contenido del documento.
2. Sospechando que el archivo podría estar ocultando datos o ser de un tipo diferente, decidí analizar su estructura interna utilizando un editor HexEd.it
3. Al ver los primeros bytes del archivo, noté que los primeros caracteres no correspondían a un PDF, sino a un PNG. 
4. Teniendo en cuenta lo anterior, procedí a cambiar la extensión del archivo de `.pdf` a `.png`. Al abrir el nuevo archivo de imagen `flag2of2-final.png`, apareció la primera mitad de la bandera: `picoCTF{f1u3n7_`.

Por último, combiné ambas partes para obtener la bandera completa:
```
picoCTF{f1u3n7_1n_pn9_&_pdf_249d05c0}
```
## **Notas adicionales
- Magic Bytes (File Signatures):** Son los primeros bytes de un archivo que identifican su formato real. Por ejemplo, `89 50 4E 47` siempre corresponde a un archivo PNG, sin importar la extensión que tenga.
- **Poliglotismo:** En seguridad, un archivo políglota es aquel que es válido para dos o más formatos diferentes al mismo tiempo, lo cual se usa a veces para evadir escaneos de seguridad.
## **Referencias
https://medium.com/@piyushbhor22/picoctf-secret-of-the-polyglot-0dc8749ca963