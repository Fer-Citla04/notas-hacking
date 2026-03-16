## **Reto**:  shark on wire 2
## **Descripción**
We found this [packet capture](https://challenge-files.picoctf.net/c_fickle_tempest/07bf5ee832c595a6de406476b6c07f164d2951fbcfcf9cf3739c25dea26e5f0b/capture.pcap). Recover the flag.

## **Solución**
Para este reto, descargué un archivo `.pcap`, que es una captura de tráfico de red. Al abrirlo con **Wireshark**, había muchos paquetes, principalmente del protocolo UDP.
Al exportar los paquetes:
1. En el paquete 32, el puerto destino es el **22** y el puerto origen es el **5000**, con el mensaje "start".
2. Más adelante, en el paquete 60, aparece el mensaje "end" con los mismos puertos.
3. Al filtrar todos los paquetes que iban al puerto destino 22, los puertos origen variaban entre el 5000 y el 5122.

Al restar 5000 a esos puertos, se obtuvo los números: el puerto 5112 se convierte en **112** (la 'p' en ASCII), el 5105 en **105** (la 'i'), el 5099 en **99** (la 'c'), y así sucesivamente. La bandera estaba escondida en los números de puerto origen.
Como completar los 35 caracteres se utilizó un script de Python con la librería **Scapy** para automatizar el resultado


`from scapy.all import *`

`Cargamos la captura de paquetes`
`packets = rdpcap('capture.pcap')`
`flag = ""`

`for p in packets:`
    `# Filtramos paquetes UDP con destino al puerto 22`
    `if p.haslayer(UDP) and p[UDP].dport == 22:`
        `# Si el puerto origen es mayor a 5000, restamos y convertimos a ASCII`
        `if p[UDP].sport > 5000:`
            `char_code = p[UDP].sport - 5000`
            `flag += chr(char_code)`

`print(flag)`

Y así se obtuvo la bandera:

```
picoCTF{p1LLf3r3d_data_v1a_st3g0}
```
## **Referencias
https://www.youtube.com/watch?v=WcMl1SvQ6hI&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=23