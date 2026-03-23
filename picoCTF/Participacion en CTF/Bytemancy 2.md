## **Descripción**
Can you conjure the right bytes? The program's source code can be downloaded [here](https://challenge-files.picoctf.net/c_lonely_island/a9e8378df77d66cf2c45ffb18555d502532defd643db631d3f538910b93ec477/app.py) Additional details will be available after launching your challenge instance.
## **Solución**
**Análisis del problema** 

Escribir "0xFF0xFF0xFF" como texto literal fallará, ya que el servidor recibiría los caracteres '0', 'x', 'F', etc. El servidor espera los **bytes crudos** (raw bytes). 

**Implementación (Payload)** 

Para enviar los bytes exactos seguidos de un salto de línea (necesario para que el servidor procese la entrada), se utiliza Python 3 para escribir directamente en el búfer de salida estándar. 

**Comando final:** 

python3 -c "import sys; sys.stdout.buffer.write(b'\xff\xff\xff\n')" | nc lonely-island.picoctf.net 59450 

**Desglose del comando:** 

1. **python3 -c**: Ejecuta código Python desde la línea de comandos. 
2. **sys.stdout.buffer.write**: Escribe datos binarios directamente, evitando que Python intente codificarlos como texto (UTF-8). 
3. **b'\xff\xff\xff\n'**: 
- b: Define una cadena de bytes. 
- \xff: El byte solicitado. 
- \n: Carácter de nueva línea (Enter) para enviar la señal de ejecución al servidor. 

4. **| (Pipe)**: Redirige la salida de Python hacia la entrada de la conexión de red.

## **Notas adicionales
- **Control de caracteres:** En la terminal, el byte 0xFF a menudo se interpreta como un carácter de control o basura visual si no se maneja correctamente. 
- **Persistencia de conexión:** Si el servidor cierra la conexión antes de mostrar la bandera, se puede añadir un retraso con (comando; sleep 1) | nc ....
- **Alternativas:** También se puede usar el comando printf en sistemas Linux: printf "\xff\xff\xff\n" | nc lonely-island.picoctf.net 59450