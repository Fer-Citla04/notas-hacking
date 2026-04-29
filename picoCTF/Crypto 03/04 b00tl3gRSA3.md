## **Reto**:  b00tl3gRSA3
## **Descripción**
Why use p and q when I can use more?Connect with nc fickle-tempest.picoctf.net 49658.
## **Solución**

┌──(kali㉿kali)-[~/Documentos/b00tl3]
└─$ nc fickle-tempest.picoctf.net 49658
c: 1351938792664835196766641515277997231059690069706927942957566407444239751044546641792425866366960850355365987808119561956844878572278026317052689436674483623840815050459928039730803982830134728538559541370018368925819148681602431953758735500003955124508699785007031776292940527868695977903978260930892834278898048151132491305506631388806983087
n: 44878081799442539268581992871690829048773572402725660435286626135550830750869576456374596354350701656403121731858888892283595926418619294537099610051017387980283398665803988817502182718128527988151629783425550547283869191833811842670179219574008898044579840819659327856558901002800532286088837491835861279113166782107909602403730366137511928807
e: 65537

1. Se factorizó el módulo n utilizando **Factordb.com**. El proceso requirió una factorización recursiva: la primera consulta arrojó una lista inicial de 25 primos,
![[Pasted image 20260429113127.png]]

2. Pero se detectó que uno de los factores de 92 dígitos todavía era un número compuesto. Tras factorizar este segundo número, obtuvimos 9 primos adicionales.
![[Pasted image 20260429113151.png]]

3. Posteriormente, calculamos la función de Carmichael $\lambda(n)$ necesaria para el RSA multi-prime. A diferencia del RSA estándar, aquí es necesario calcular el Mínimo Común Múltiplo  de todos los $(p_i - 1)$, por lo que implementamos una función en Python para iterar sobre los 34 factores y obtener el MCM acumulado. 
from math import gcd

`#Valores proporcionados `
`c = 1351938792664835196766641515277997231059690069706927942957566407444239751044546641792425866366960850355365987808119561956844878572278026317052689436674483623840815050459928039730803982830134728538559541370018368925819148681602431953758735500003955124508699785007031776292940527868695977903978260930892834278898048151132491305506631388806983087`
`n = 44878081799442539268581992871690829048773572402725660435286626135550830750869576456374596354350701656403121731858888892283595926418619294537099610051017387980283398665803988817502182718128527988151629783425550547283869191833811842670179219574008898044579840819659327856558901002800532286088837491835861279113166782107909602403730366137511928807`
`e = 65537`

`factors = [`
    `# Factores de la primera imagen`
    `8620808501, 8621706083, 8622165913, 8935539667, 8960100953,` 
    `9055897469, 9175250629, 9556454329, 9785152549, 10089125353,` 
    `13547136061, 13730986847, 13852006853, 14001873287, 14123177221,` 
    `14634495719, 14772456359, 14886249047, 15325372421, 15575486039,` 
    `16037379577, 16103810399, 16676893333, 16749571463, 16992625679,`

    `11734756237, 13250426531, 13618066129, 14064131437, 14624021047,` 
    `14688539531, 14894106551, 15275393461, 15977204921`
`]`

`def get_lcm(a, b):`
    `return abs(a * b) // gcd(a, b)`

`def solve():`
    `# Paso 1: Calcular el Mínimo Común Múltiplo de (p-1) para todos los factores`
    `# Esto es lambda(n), necesario para encontrar d en RSA multi-prime`
    `phi_n = factors[0] - 1`
    `for p in factors[1:]:`
        `phi_n = get_lcm(phi_n, p - 1)`
    
    `# Paso 2: Calcular el exponente privado d`
    `# d = e^(-1) mod phi_n`
    `try:`
        `d = pow(e, -1, phi_n)`
        
        `# Paso 3: Descifrar el mensaje`
        `# m = c^d mod n`
        `m = pow(c, d, n)`
        
        `# Paso 4: Convertir el número resultante a texto ASCII`
        `final_hex = hex(m)[2:]`
        `# Ajustar si el hex tiene una longitud impar`
        `if len(final_hex) % 2 != 0:` 
            `final_hex = '0' + final_hex`
            
        `flag = bytes.fromhex(final_hex).decode('utf-8')`
        `print(flag)`
    `except Exception as error:`
        `print(f"Error al descifrar: {error}")`

`if __name__ == "__main__":`
    `solve()`
    
```
picoCTF{too_many_fact0rs_3023548}
```

## **Notas adicionales
- RSA Multi-prime: Es una variante de RSA que utiliza más de dos factores primos para formar el módulo $n$. Aunque permite operaciones de descifrado más rápidas mediante el Teorema del Resto Chino, facilita la factorización si los primos elegidos son pequeños o conocidos en bases de datos.

## **Referencias 
https://factordb.com/