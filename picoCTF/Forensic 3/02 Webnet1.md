## **Reto**:  Webnet1
## **Descripción**
We found this [packet capture](https://challenge-files.picoctf.net/c_fickle_tempest/d1e9add4e31989553f239ebf71ba5972f9bed7bd4932f931e14bfba80d75f815/capture.pcap) and [key](https://challenge-files.picoctf.net/c_fickle_tempest/d1e9add4e31989553f239ebf71ba5972f9bed7bd4932f931e14bfba80d75f815/picopico.key). Recover the flag.
## **Solución**

1. Al igual que en WebNet0, fui a **Edit -> Preferences -> Protocols -> TLS** y agregué la llave `picokey.pem` en la lista de llaves .
2. Inmediatamente, el tráfico cambió a color verde.
3. Al revisar los paquetes, noté que en el paquete 47 se realizaba una petición **HTTP GET** para descargar una imagen.
4. Revisé las cabeceras (headers) del paquete y vi un campo que decía `Pico-Flag`, pero al probarlo me di cuenta de que era una **bandera falsa** diseñada para despistar.
5. Fui al menú File -> Export Objects -> HTTP. Esto me permitió ver todos los archivos que se descargaron durante la sesión.
6. Seleccioné la imagen del paquete 47 y la guardé en mi carpeta de trabajo.
7. Ejecuté el comando `strings` sobre la imagen descargada: `strings vultu.jpg | grep picoCTF`
8. El comando filtró el ruido y me entregó la bandera verdadera que estaba escondida al final del archivo de imagen.

```
picoCTF{honey.roasted.peanuts}
```


## **Referencias
https://www.youtube.com/watch?v=Ym3i79nEHjw&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=25