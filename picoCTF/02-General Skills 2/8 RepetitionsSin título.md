## **Reto**: 8 ->  Repetitions

## **Descripción**
Can you make sense of this file?Download the file [here](https://artifacts.picoctf.net/c/474/enc_flag).
## **Solución**
- Primero al abrir el archivo del reto, me encontré con un bloque de texto que no tenía sentido, pero noté algo clave: terminaba en caracteres `==`. Esto me indicó de inmediato que el archivo estaba codificado en **Base64**
- Luego Intenté decodificarlo una vez, pero el resultado era otro código similar. Entendí entonces que la bandera estaba envuelta en múltiples capas de codificación, como una cebolla. Para resolverlo, utilicé "tuberías" para pasar el resultado de una decodificación a la siguiente de forma consecutiva.
- Para pelar todas las capas (que resultaron ser 6 en total), ejecuté este comando en mi terminal:

**cat enc_flag | base64 --decode | base64 --decode | base64 --decode | base64 --decode | base64 --decode | base64 --decode**

Al final de esta cadena, el sistema por fin soltó la bandera:

```
picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_3f81f7be}
```

## **Notas adicionales**
- **cat**: Abre y lee el contenido del archivo original.
- **| (Pipe)**: Funciona como un puente; toma la respuesta de un comando y se la entrega al siguiente.
- **base64 --decode**: Es la herramienta que traduce el código Base64 a texto normal.
Aunque el método manual funciona, también existe una forma más sencilla y rápida de saber cuál es la bandera en python con el siguiente código:

```
import base64

with open('enc_flag') as file:
   data = file.read()
while 'picoCTF' not in str(data):
   data = base64.b64decode(data)

print(data)
```
