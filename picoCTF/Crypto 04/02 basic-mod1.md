## **Reto**:  basic-mod1
## **Descripción**
We found this weird message being passed around on the servers, we think we have a working decryption scheme.Download the message [here](https://artifacts.picoctf.net/c/128/message.txt).Take each number mod 37 and map it to the following character set: 0-25 is the alphabet (uppercase), 26-35 are the decimal digits, and 36 is an underscore.Wrap your decrypted message in the picoCTF flag format (i.e. `picoCTF{decrypted_message}`)
## **Solución**
1. El reto requiere procesar una lista de números aplicando una operación de módulo 37 a cada uno y mapear el resultado según el siguiente conjunto de caracteres:

- **0-25**: Alfabeto en mayúsculas (A-Z).

- **26-35**: Dígitos decimales (0-9).

- **36**: Guion bajo (_).

2. Se crea un script que lee el contenido de message.txt, separa los números y calcula el residuo de cada uno respecto a 37.

d`ef decode(number):`
    `return number % 37`

`def main():`
    `# Leer los números del archivo message.txt`
    `with open("message.txt", "r", encoding="UTF-8") as f:`
        `lst = f.read().split()`
    
    `dec_lst = []`
    `for i in range(len(lst)):`
        `dec_lst.append(decode(int(lst[i])))`
    
    `print(f"Valores decodificados: {dec_lst}")`

`if __name__ == '__main__':`
    `main()`

3. Al ejecutarlo se obtuvo la siguiente secuencia de valores decodificados: 
   `[17, 26, 20, 13, 3, 36, 13, 36, 17, 26, 20, 13, 3, 36, 1, 32, 1, 28, 31, 31, 29, 27]`
4. Por último, procedimos al realizar el mapeo:
   `[R, 0, U, N, D, _, N, _, R, 0, U, N, D, _, B, 6, B, 2, 5, 5, 3, 1]`

```
picoCTF{R0UND_N_R0UND_B6B25531}
```
## **Notas adicionales
- Mapeo de Caracteres: Este reto utiliza un sistema de sustitución simple basado en índices. Es fundamental seguir el orden exacto del conjunto de caracteres (letras, luego números, luego símbolos) para evitar errores en la traducción de la bandera.