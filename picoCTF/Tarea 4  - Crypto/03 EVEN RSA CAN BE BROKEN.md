## **Reto**: EVEN RSA CAN BE BROKEN???
## **Descripción**
This service provides you an encrypted flag. Can you decrypt it with just N & e?

Connect to the program with netcat:

$ nc verbal-sleep.picoctf.net 55074

The program's source code can be downloaded here.
## **Solución**
1. Primero ejecutamos el comando nc verbal-sleep.picoctf.net 55074
2. Datos obtenidos

N (Módulo): 25677895999088848130035110145861569837272952864056704268600182931128983590655584398566490275662284613534846508535172338522964904811309023974147713377633686

e (Exponente público): 65537

Ciphertext (c): 7731151163090820731027311608732752827393955665400194137781167750367819143605140568436906397967666105639861202415242243657021116337737213187004336036049901

3. 
- **Factorización de $N$**: Al ser $p = 2$, calculamos el segundo factor como $q = N / 2$.
- **Función Totiente ($\phi$)**: Se simplifica a $\phi(N) = (2 - 1)(q - 1) = q - 1$.
- **Clave Privada ($d$)**: Se calculó como el inverso modular de $e$ respecto a $\phi(N)$ mediante la operación $d \equiv e^{-1} \pmod{\phi(N)}$.
  
4. Debido a un error de entorno en Kali, se desarrolló un script en Python que no depende de librerías externas (pycryptodome), utilizando funciones nativas para garantizar la ejecución.

`N = 25677895999088848130035110145861569837272952864056704268600182931128983590655584398566490275662284613534846508535172338522964904811309023974147713377633686`
`e = 65537`
`c = 7731151163090820731027311608732752827393955665400194137781167750367819143605140568436906397967666105639861202415242243657021116337737213187004336036049901`

`#Factorización inmediata`
`p = 2`
`q = N // p`
`phi = q - 1`

`#Derivación de la clave privada y descifrado`
`d = pow(e, -1, phi)`
`m = pow(c, d, N)`

 `#Conversión a texto ASCII`
`hex_m = hex(m)[2:]`
`if len(hex_m) % 2 != 0: hex_m = '0' + hex_m`
`flag = bytes.fromhex(hex_m).decode('ascii', errors='ignore')`

`print(f"Resultado: {flag}")`

5. Finalmente, ejecutamos el script en la terminal y así conseguimos la bandera
```
 picoCTF{tw0_1$_pr!m3df98b648}
```
## **Notas adicionales**
En RSA, $N$ debe ser el producto de dos números primos grandes ($p$ y $q$). Como todos los primos mayores a 2 son impares, $N$ siempre debe ser un número impar.