## **Reto**:  ReadMyCert
## **Descripción**
How about we take you on an adventure on exploring certificate signing requestsTake a look at this CSR file [here](https://artifacts.picoctf.net/c/422/readmycert.csr).
## **Solución**
1. Utilizamos el comando `file` para confirmar la integridad del archivo, el cual reveló que se trata de una solicitud de certificado en formato PEM. Posteriormente, visualizamos el contenido con el comando `cat readmycert.csr`.
2. Para extraer la información legible del archivo, empleamos la herramienta **OpenSSL**, ejecutando el siguiente comando:
`openssl req -in readmycert.csr -noout -text`

3. Al analizar el desglose identificamos que la bandera se encontraba embebida directamente en el atributo **CN**.

```
picoCTF{read_mycert_373b4ab0}
```
## **Notas adicionales
- CSR (Certificate Signing Request): Es un estándar utilizado para solicitar certificados digitales. Contiene la clave pública y datos de identificación como el nombre de dominio y la organización.