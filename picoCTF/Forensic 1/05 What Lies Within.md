## **Reto**:  What Lies Within
## **Descripción**
There's something in the [building](https://challenge-files.picoctf.net/c_fickle_tempest/c0eec6af0f04316e2bdc4a9f095afd0e2d0121f5e543dbc4a65bb0038d72a993/buildings.png). Can you retrieve the flag?

## **Solución**
Para hacerlo utilicé `zsteg`. Ejecuté el siguiente comando en la terminal de Kali Linux:

`zsteg -a buildings.png`

Y así me dió la bandera de este reto:

```
picoCTF{h1d1ng_1n_th3_b1t5}
```
## **Referencias
https://www.youtube.com/watch?v=bFUB-USG3sw&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=18