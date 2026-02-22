## **Reto**: 10°-> Nice netcat...

## **Descripción**
There is a nice program that you can talk to by using this command in a shell:

Additional details will be available after launching your challenge instance.

## **Solución**
Lo que hice en este reto fue que hice clic en launch instance y me salió lo siguiente:
nc wily-courier.picoctf.net 65448

Ese mismo comando lo pegué en la terminal de linux y me dió la siguiente serie de numeros:
112 
105 
99 
111 
67 
84 
70 
123 
103 
48 
48 
100 
95 
107 
49 
116 
116 
121 
33 
95 
110 
49 
99 
51 
95 
107 
49 
116 
116 
121 
33 
95 
101 
57 
99 
56 
53 
125 
10 
Después ingresé el siguiente comando para que python lo convirtiera de decimal a Ascii
┌──(kali㉿kali)-[~]
└─$ python3 -c "print(''.join([chr(int(x)) for x in '112 105 99 111 67 84 70 123 103 48 48 100 95 107 49 116 116 121 33 95 110 49 99 51 95 107 49 116 116 121 33 95 101 57 99 56 53 125'.split()]))"

```
picoCTF{g00d_k1tty!_n1c3_k1tty!_e9c85}
```

## **Notas adicionales**
También se pudo haber resuelto en cyberchef (para una alternativa menos complicada) poniendo el mensaje en from decimal y lo convertía a Ascii.
