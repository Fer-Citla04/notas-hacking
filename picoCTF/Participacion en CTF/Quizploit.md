## **Reto**:  Quizploit
## **Descripción**
Solve the quiz.Download the source code to answer questions [here](https://challenge-files.picoctf.net/c_lonely_island/68da2b87534a701611b5fce7138e8afe09c9ff50a5837da106fad1289e8e683a/vuln.c).Download the binary to answer questions [here](https://challenge-files.picoctf.net/c_lonely_island/68da2b87534a701611b5fce7138e8afe09c9ff50a5837da106fad1289e8e683a/vuln).Connect with the challenge instance here: `nc lonely-island.picoctf.net 61806`

## **Solución**
Este reto consistió en un cuestionario interactivo vía `nc` (Netcat). Para responder correctamente, tuve que analizar el código fuente en C y el archivo binario utilizando herramientas de ingeniería inversa y análisis de sistemas.

A continuación, detallo los puntos clave que analicé para obtener el puntaje perfecto:

1. **Análisis de Arquitectura:** Utilicé el comando `file` para confirmar que el binario es un **ELF de 64 bits**. Esto es crucial porque define el tamaño de los registros y las direcciones de memoria.

2. **Vulnerabilidad de Memoria:** Al revisar la función `vuln()`, noté que declaraba un buffer de **0x15 bytes** (21 en decimal), pero la función `fgets` permitía leer hasta **0x90 bytes** (144 en decimal).

- **Cálculo del Overflow:** $0x90 - 0x15 = 0x7b$ bytes de desbordamiento posibles. Esto confirma una vulnerabilidad de **Buffer Overflow**.

3. **Protecciones del Binario:** Usé la herramienta `checksec` para revisar las defensas:
    - **NX (No-eXecute):** Está habilitado, lo que significa que no puedo ejecutar shellcode directamente en el stack. La técnica para saltarse esto sería **ROP (Return Oriented Programming)**.
    - **Stripped:** El binario **no estaba "stripped"**, lo que facilitó ver los nombres de las funciones como `win()` y `vuln()`.

4. **Función Oculta:** Identifiqué una función llamada `win()` que no se llama en ninguna parte del flujo normal del programa. Usando `objdump -d metadata | grep win`, localicé su dirección de memoria exacta: `0x401176`.

Al contestar las 13 preguntas con esta información, el servidor validó mi conocimiento técnico y me entregó la bandera final.

```
picoCTF{my_bIn@4y_3xpl0it_fL@g_0969fdeb}
```