## **Reto**:  Ph4nt0m 1ntrud3r
## **Descripción**
A digital ghost has breached my defenses, and my sensitive data has been stolen! 😱💻 Your mission is to uncover how this phantom intruder infiltrated my system and retrieve the hidden flag.To solve this challenge, you'll need to analyze the provided PCAP file and track down the attack method. The attacker has cleverly concealed his moves in well timely manner. Dive into the network traffic, apply the right filters and show off your forensic prowess and unmask the digital intruder!Find the PCAP file here [Network Traffic PCAP file](https://challenge-files.picoctf.net/c_verbal_sleep/960abba2fdbc9be5013ef87f1df67213e9b63d4561d7a8c8c1ce7a4ce40a547e/myNetworkTraffic.pcap) and try to get the flag.
## **Solución**
1. Primero, descargué el archivo. Al tratarse de un archivo `.pcap`, utilicé **TShark**, la versión de línea de comandos de Wireshark, para realizar una inspección.
2. Para extraer la información, utilicé filtros específicos que me permitieran ver únicamente los datos útiles de los segmentos TCP, los cuales aparecieron inicialmente como cadenas hexadecimales.
3. Teniendo en cuenta lo anterior, busqué filtrando por longitudes de paquete específicas 12 y 4 bytes. Utilicé el siguiente comando para extraer y convertir esos datos de hexadecimal a texto ASCII :

`tshark -r myNetworkTraffic.pcap -Y "tcp.len==12 || tcp.len==4" -T fields -e tcp.segment_data | xxd -r -p`

4. El resultado fue una serie de cadenas en Base64. Al decodificar cada fragmento de forma independiente, obtuve piezas de texto como `picoCTF`, `{1t_w4s`, `_34sy_t`
5. Por último, dado que las piezas estaban desordenadas, apliqué lógica de gramática para rearmar la bandera. Aunque los primeros intentos falló, el orden reveló el mensaje "It wasn't that easy, to be honest".
```
picoCTF{1t_w4snt_th4t_34sy_tbh_4r_e5e8c78d}
```
## **Notas adicionales
- **TShark:** Es una herramienta poderosa para el análisis de red en terminal que permite filtrar tráfico masivo mediante expresiones booleanas (como `||` para "o").
- **xxd -r -p:** Este comando es para "revertir" un volcado hexadecimal y convertirlo en caracteres de texto o binarios originales.
