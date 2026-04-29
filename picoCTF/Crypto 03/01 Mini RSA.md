## **Reto**:  Mini RSA
## **Descripción**
What happens if you have a small exponent? There is a twist though, we padded the plaintext so that (M ** e) is just barely larger than N. Let's decrypt this:[values](https://challenge-files.picoctf.net/c_wily_courier/1279f9e9d2d949e0ff290d65cc419ffb531cf73732f770725b10c12a490344fc/values)

## **Solución**
1. Extraemos los datos del archivo proporcionado: el módulo N (un número de 1024 bits), el exponente e=3 y el ciphertext C. 
2. Instalamos el siguiente paquete para la solución 

`sudo apt update && sudo apt install python3-gmpy2 -y`

3. Desarrollamos un script en Python  para iterar sobre posibles valores de k . En cada iteración, sumamos el múltiplo actual de N al ciphertext y utilizamos la función `gmpy2.iroot` para verificar si el resultado tiene una raíz cúbica exacta. 


`import gmpy2`

`#Datos extraídos de 'values'`
`n = 161576568432...` 
`c = 570972017502...` 
`e = 3`

`def resolver():`
    `for k in range(2000):`
        `m_cubed = c + (k * n)`
        `m, exacto = gmpy2.iroot(m_cubed, 3)`
        `if exacto:`
            `print(f"¡Encontrado con k = {k}!")`
            `flag = bytes.fromhex(hex(m)[2:]).decode()`
            `print(f"LA FLAG ES: {flag}")`
            `return`
`resolver()`


4. Al ejecutarlo, el programa identificó el valor correcto de k y el script convirtió el número decimal resultante a hexadecimal y luego a texto ASCII para revelar la bandera

```
picoCTF{e_sh0u1d_b3_lArg3r_92f4d5a5}
```
