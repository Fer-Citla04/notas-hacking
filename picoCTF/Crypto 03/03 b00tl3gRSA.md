## **Reto**:  b00tl3gRSA
## **Descripción**
In RSA d is a lot bigger than e, why don't we use d to encrypt instead of e?Connect with nc fickle-tempest.picoctf.net 54147.

## **Solución**
1. La descripción del reto sugiere una implementación incorrecta de RSA donde se utiliza el exponente privado d de forma inadecuada o se elige un valor para este que compromete la seguridad. 
2. Si el exponente privado d es pequeño, el sistema es vulnerable al Ataque de Wiener. 
3. Con los valores proporcionados por el servidor (el módulo N, el exponente público e y el ciphertext C) desarrollamos un script que implementa la búsqueda de convergentes de la fracción e/n para encontrar el exponente privado:


`from math import isqrt`

`def continued_fraction(num, den):`
    `cf = []`
    `while den:`
        `a = num // den`
        `cf.append(a)`
        `num, den = den, num - a * den`
    `return cf`

`def convergents(cf):`
    `k_prev, k_curr = 0, 1`
    `d_prev, d_curr = 1, 0`
    `for a in cf:`
        `k_next = a * k_curr + k_prev`
        `d_next = a * d_curr + d_prev`
        `k_prev, k_curr = k_curr, k_next`
        `d_prev, d_curr = d_curr, d_next`
        `yield k_curr, d_curr`

`def wiener_attack(e, n):`
    `cf = continued_fraction(e, n)`
    `for k, d in convergents(cf):`
        `if k == 0 or (e * d - 1) % k != 0:`
            `continue`
        `phi = (e * d - 1) // k`
        `b = n - phi + 1`
        `D = b*b - 4*n`
        `if D >= 0:`
            `s = isqrt(D)`
            `if s*s == D:`
                `p, q = (b + s) // 2, (b - s) // 2`
                `if p*q == n:`
                    `return d`
    `return None`

 #`Ejecución del ataque y descifrado`
`d = wiener_attack(e, n)`
`m = pow(c, d, n)`
`print(m.to_bytes((m.bit_length()+7)//8, "big"))`


Al ejecutar el script el resultado fue una cadena `cGljb0NURntiYWRfMWQzYTVfMzgwMTI1NX0=`. Finalmente, decodificamos el string para obtener la bandera
```
picoCTF{bad_1d3a5_3801255}   
```
## **Notas adicionales
- Ataque de Wiener: este ataque matemático utiliza fracciones continuas para recuperar $d$ a partir únicamente de los valores públicos $(e, n)$. Michael Wiener demostró en 1990 que si $d < \frac{1}{3} n^{1/4}$, la clave privada puede ser recuperada en segundos.
