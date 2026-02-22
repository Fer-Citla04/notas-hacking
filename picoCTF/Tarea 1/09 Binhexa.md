## **Reto**: Binhexa

## **Descripción**
How well can you perfom basic binary operations? Start searching for the flag here `nc titan.picoctf.net 53163`

## **Solución**
1. Primero, me conecté al servidor usando el comando `nc titan.picoctf.net 53163`.
2. El sistema me entregó dos números binarios :
- **Número 1:** `10110110`
- **Número 2:** `00101000`
3. Luego, me pidió realizar 6 operaciones lógicas y matemáticas en orden. Utilicé calculadoras binarias  para asegurar los resultados:

- **Pregunta 1 (Right Shift `>>`):** Desplacé el Número 2 un bit a la derecha. Resultado: `00010100`.
- **Pregunta 2 (Suma `+`):** Sumé el Número 1 y el Número 2. Resultado: `11011110`.
- **Pregunta 3 (Left Shift `<<`):** Desplacé el Número 1 un bit a la izquierda. Resultado: `101101100`.
- **Pregunta 4 (OR `|`):** Operación lógica OR entre ambos números. Resultado: `10111110`.
- **Pregunta 5 (AND `&`):** Operación lógica AND entre ambos números. Resultado: `00100000`.
- **Pregunta 6 (Multiplicación `*`):** Multipliqué ambos números binarios. Resultado: `1110001110000`.

4. Finalmente, el reto me pidió convertir el resultado de la última operación (`1110001110000`) a hexadecimal.
5. Usé un conversor de binario a hexadecimal y obtuve el valor: `1C70`.
6. Y así fue como obtuve la bandera.
```
picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_1367e2c6}
```

## **Referencias**
https://miniwebtool.com/es/calculadora-binario/?number1=00101000&operate=shr&number2=00000001
https://miniwebtool.com/es/calculadora-binario/?number1=10110110&operate=add&number2=00101000
https://miniwebtool.com/es/calculadora-binario/?number1=10110110&operate=shl&number2=00000001
https://miniwebtool.com/es/calculadora-binario/?number1=10110110&operate=or&number2=00101000
https://miniwebtool.com/es/calculadora-binario/?number1=10110110&operate=and&number2=00101000
https://miniwebtool.com/es/calculadora-binario/?number1=10110110&operate=mul&number2=00101000
https://www.rapidtables.com/convert/number/binary-to-hex.html?x=1110001110000