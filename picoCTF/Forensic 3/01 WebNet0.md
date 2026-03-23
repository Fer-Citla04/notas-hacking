## **Reto**:  WebNet0
## **Descripción**
We found this [packet capture](https://challenge-files.picoctf.net/c_fickle_tempest/66113619363fca174ef6bf56587007af1626f99c44fc5cf92333f9fd8876ce9a/capture.pcap) and [key](https://challenge-files.picoctf.net/c_fickle_tempest/66113619363fca174ef6bf56587007af1626f99c44fc5cf92333f9fd8876ce9a/picopico.key). Recover the flag.
## **Solución**
Para este reto, descargué una captura de paquetes (`.pcap`) y un archivo de llave privada (`.pem`). Después, abrí la captura en **Wireshark**.

Como el reto nos proporcionó la llave privada RSA, se resolvió de la sig manera:

1. Fui al menú **Edit -> Preferences -> Protocols -> TLS**.
2. En la sección de **RSA keys list**, hice clic en **Edit** y luego en el símbolo de **+** para agregar una nueva entrada.
3. Cargué el archivo `picokey.pem` en el apartado de **Key File**.
        
Después:
1. Al aplicar la llave, Wireshark cambió el color de muchos paquetes a verde o azul claro.
2. Para encontrar la bandera, usé la función de búsqueda con ctrl + F, seleccioné "Packet details" y busqué la cadena "picoCTF".
3. Wireshark me llevó a un paquete HTTP que contenía la respuesta del servidor. Al ver los detalles del flujo, la bandera apareció.

```
picoCTF{nongshim.shrimp.crackers}
```

## **Notas adicionales

También esto se puede automatizar en la terminal de Linux usando `ssldump`: `ssldump -r capture.pcap -k picokey.pem -d | grep picoCTF`


## **Referencias
https://www.youtube.com/watch?v=9uflLPoETOc&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=24