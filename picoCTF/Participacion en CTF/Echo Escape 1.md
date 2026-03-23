## **Reto**: Echo Escape 1
## **Descripción**
The "secure" echo service welcomes you politely… but what if you don’t stay polite? Can you make it reveal the hidden flag? You can download the program file [here](https://challenge-files.picoctf.net/c_mysterious_sea/04b7d130bb78ee1001be132ebd4f4b09734bad6d543aa10252bbb627ddca58c3/vuln) and source [code](https://challenge-files.picoctf.net/c_mysterious_sea/04b7d130bb78ee1001be132ebd4f4b09734bad6d543aa10252bbb627ddca58c3/vuln.c).Connect to the program with netcat: `nc mysterious-sea.picoctf.net 53969`.
## **Solución**
Para este reto, analicé el código fuente `vuln.c` y encontré una vulnerabilidad clásica de desbordamiento de búfer. El programa reserva un espacio pequeño en la memoria, pero permite que el usuario introduzca mucha más información de la que cabe, lo que nos permite "ensuciar" otras partes de la memoria.

Estos fueron los pasos que seguí para explotar el programa:

**1. Análisis del código (El "Culpable")** En la función `main`, encontré una contradicción fatal:

- **Espacio reservado:** Se creó un búfer llamado `buf` de solo **32 bytes**.
    
- **Entrada permitida:** La función `read(0, buf, 128)` permitía escribir hasta **128 bytes**.
    
- **La oportunidad:** Tenía **96 bytes** de exceso para desbordar la memoria y sobrescribir el flujo del programa.
    

**2. Identificar el objetivo (La función win)** Revisando el código, vi una función llamada `win()` que lee el archivo `flag.txt`. Sin embargo, en el flujo normal, esta función nunca es llamada. Mi objetivo era desviar el programa para que, al terminar, saltara directamente a esa función.

**3. Localizar el destino (Dirección de memoria)** Utilicé el comando `nm` (o también se puede usar `objdump`) para encontrar la dirección exacta donde reside la función `win`.

- **Resultado:** La dirección era `0x401256`.
    

**4. Construcción del Payload (La carga útil)** Para tomar el control, tuve que llenar la pila (stack) como si fuera un vaso de agua que se desborda hasta llegar al "interruptor" que controla a dónde va el programa (llamado **Return Address**).

- **32 bytes de basura:** Para llenar el búfer `buf`.
    
- **8 bytes de basura extra:** Para saltar el registro **RBP** (la base de la pila en sistemas de 64 bits).
    
- **La dirección de win:** Escrita en formato **Little Endian** (`\x56\x12\x40\x00\x00\x00\x00\x00`).
    

**5. Ejecución final** Envié los 40 bytes de basura seguidos de la dirección de `win` a través de la red usando `nc`. El servidor recibió los datos, el búfer se desbordó, la dirección de retorno se cambió por la de `win`, y el servidor me entregó la bandera.

```
picoCTF{3ch0_s3rv1c3_br34k5_d51d6163}
```
## **Notas adicionales
- **Stack Overflow:** Consiste en llenar la pila más allá de sus límites para alterar datos críticos.

- **Little Endian:** Es la forma en que las arquitecturas x86 (como la de tu escuela) leen las direcciones de memoria: del byte menos significativo al más significativo (de atrás hacia adelante).

- **Instruction Pointer (RIP/EIP):** Es el registro del procesador que dice "esta es la siguiente instrucción que voy a ejecutar". Al sobrescribir la dirección de retorno, manipulamos este puntero.
