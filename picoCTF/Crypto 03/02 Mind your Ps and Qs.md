## **Reto**:  Mind your Ps and Qs
## **Descripción**
In RSA, a small e value can be problematic, but what about N? Can you decrypt this?[values](https://challenge-files.picoctf.net/c_wily_courier/4540a62876bdb4e341c70e3300408ced0ae02e4d27bb41b747a80f42aef919ba/values)
## **Solución**
1. Primero descargamos el archivo con el comando wget y visualizamos su contenido con cat. 
2. Para encontrar d, se tiene que factorizar el módulo N en sus componentes p y $q$. Pero como el valor de N es  pequeño, utilizamos la herramienta dCode para factorizarlo
3. . Los valores obtenidos fueron:

- **p:** $1891771437429478964908181306574287207137$
    
- **q:** $501332739776173570344039681219489434626477$
    

4. Luego, hacemos un script utilizando la librería Crypto.Util.number para realizar el descifrado. 


`from Crypto.Util.number import inverse, long_to_bytes`

`n = 948406957756830799684818171639547165784816468744946013083947881743680617123566349`
`e = 65537`
`c = 15341890103764929939105506004034128738090325640037083301857608662849501626260517`
`p = 1891771437429478964908181306574287207137`
`q = 501332739776173570344039681219489434626477`

`phi = (p - 1) * (q - 1)`
`d = inverse(e, phi)`

`#Desencriptar: c^d mod n = m`
`m = pow(c, d, n)`
`print(long_to_bytes(m))`


Al ejecutar el código, obtuvimos el mensaje: `b'\n}19ea7cd1_do0g_0n_N_11ams{FTCocip'`, pero este está invertido, así que utilizamos Reverse Writing para reordenar los caracteres:

```
picoCTF{sma11_N_n0_g0od_1dc7ae91}
```
## **Notas adicionales
- **Factorización de N**: La seguridad de RSA reside en la dificultad de factorizar $N$. Si $N$ no es lo suficientemente grande, puede ser vulnerado mediante bases de datos de factores o algoritmos de factorización rápida.
