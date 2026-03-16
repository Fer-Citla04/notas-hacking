## **Reto**:   shark on wire 1
## **Descripción**
We found this [packet capture](https://challenge-files.picoctf.net/c_fickle_tempest/134d2a2cf6ec5b7e757effc9b32977af7cc324b8e99a5ddb64737794a14dc18d/capture.pcap). Recover the flag.
## **Solución**

Para resolver este reto, descargué un archivo `.pcap`, que contiene una captura de tráfico de red. 
Luego, utilicé **Wireshark**. Al abrir la captura, vi una gran cantidad de paquetes, especialmente del protocolo **UDP**. A diferencia de TCP, UDP no establece una conexión formal ni verifica si los datos llegaron, simplemente los envía.
1. Seleccioné uno de los paquetes UDP y utilicé la función **"Follow UDP Stream"** . 
2. Fui cambiando el número del stream en el filtro para revisar las diferentes conversaciones.
3. En el **Stream 4**, la información no era relevante. Sin embargo, al cambiar al **Stream 6**, apareció una cadena de texto con el formato característico de las banderas de picoCTF.

```
picoCTF{StaT31355_636f6e6e}
```


## **Referencias
https://www.youtube.com/watch?v=q8cM4sY0izw&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=16