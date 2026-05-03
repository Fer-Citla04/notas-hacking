## **Reto**: Crack the Power
## **Descripción**
We received an encrypted message. The modulus is built from primes large enough that factoring them isn’t an option, at least not today. See if you can make sense of the numbers and reveal the flag.Download the [message](https://challenge-files.picoctf.net/c_amiable_citadel/064d4179839d2d7423ffdb19ce407b8ab56ac27afbb579983a98ced35a174ea4/message.txt).
## **Solución**
1. Descargamos el archivo `message.txt` mediante el comando `wget`. Al examinar su contenido con cat, obtuvimos los parámetros del cifrado RSA: un módulo N, e y el mensaje cifrado $C$.
2. Como el exponente $e$ es bajo en comparación con los estándares de seguridad.
3. Debido a que las calculadoras convencionales no pueden manejar raíces de números tan grandes, desarrollamos un script en Python que implementa un algoritmo de búsqueda binaria para encontrar la raíz 

`def get_root(n, nth):`
    `# Algoritmo de búsqueda binaria para encontrar la raíz exacta`
    `low = 0`
    `high = n`
    `ans = 0`
    `while low <= high:`
        `mid = (low + high) // 2`
        `if mid**nth <= n:`
            `ans = mid`
            `low = mid + 1`
        `else:`
            `high = mid - 1`
    `return ans`
 `#Datos extraídos de message.txt`
`e = 20`
`c = 64063743081040685750... # (Valor truncado para la documentación)`

`#1. Extraer la raíz 20-ava de c`
`m = get_root(c, e)`

`#2. Convertir el entero resultante a texto ASCII`
`try:`
    `h = hex(m)[2:]` 
    `if len(h) % 2 != 0: h = '0' + h` 
    `flag = bytes.fromhex(h).decode('ascii')`
    `print(f"FLAG: {flag}")`
`except:`
    `print("Error al decodificar")`

4. Al ejecutar el script con el comando python3 sol.py, el programa calculó la raíz exacta, la cual fue convertida de formato hexadecimal a texto ASCII, revelando así la bandera 

```
picoCTF{t1ny_e_4da5fb4d}
```

## **Referencias**
https://medium.com/@chinonsopeter456/crack-the-power-d8f5cccf707c