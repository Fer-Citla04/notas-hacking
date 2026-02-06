## **Reto**: 8°-> Plumbing

## **Descripción**
Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag?

Additional details will be available after launching your challenge instance.
## **Solución**
En kali pegué lo que me dieron al iniciar instancia:
nc saturn.picoctf.net 64441 
y me dio lo siguiente:
'picoCTF{gl17ch_m3_n07_' + chr(0x61) + chr(0x34) + chr(0x33) + chr(0x39) + chr(0x32) + chr(0x64) + chr(0x32) + chr(0x65) + '}'

Entonces precedí a instalar python porque éste actúa como un tipo traductor:
(kali㉿kali)-[~/mis_retos]
└─$ python3 -c "print('picoCTF{gl17ch_m3_n07_' + chr(0x61) + chr(0x34) + chr(0x33) + chr(0x39) + chr(0x32) + chr(0x64) + chr(0x32) + chr(0x65) + '}')"
```
picoCTF{gl17ch_m3_n07_a4392d2e}
```
## **Referencias**
Kali linux
Python3