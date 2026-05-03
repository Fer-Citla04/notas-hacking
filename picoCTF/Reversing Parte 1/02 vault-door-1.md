## **Reto**:  vault-door-1
## **Descripción**
This vault uses some complicated arrays! I hope you can make sense of it, special agent. The source code for this vault is here: [VaultDoor1.java](https://challenge-files.picoctf.net/c_fickle_tempest/df83732fa379fb7cf3373e872748a40ec53c5baa532f3274e1ab499cd3d3b197/VaultDoor1.java)
## **Solución**
1. Para resolver el reto primero, visualicé el archivo para entender cómo se validaba la contraseña. 
2. Inserté el comando `cat VaultDoor1.java`
3. Para trabajar solo con las líneas que contenían los caracteres de la bandera, guardé el resultado en un archivo temporal llamado `indices.txt`.
   `cat VaultDoor1.java | grep "password.charAt" > indices.txt`
4. Por último encontré la bandera con el comando `cat indices.txt | sed 's/.*(\(.*\)).*== '\''\(.*\)'\''.*/\1 \2/' | sort -n | awk '{print $2}' | tr -d '\n'`
5. El comando te devolvió la cadena de texto ya ordenada: `d35cr4mbl3_tH3_cH4r4cT3r5_1ef266`

```
picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_1ef266}
```
## **Notas adicionales
- **`sed`**: Utiliza expresiones regulares para buscar el número entre paréntesis y el carácter entre comillas simples, eliminando todo lo demás de la línea.
- **`sort -n`**: Ordena las líneas numéricamente basasdo en el índice (0, 1, 2... 31).
- **`awk '{print $2}'`**: Selecciona únicamente la segunda columna, que correspondía al carácter de la contraseña.
- **`tr -d '\n'`**: Elimina los saltos de línea para que todos los caracteres se imprimieran juntos en una sola cadena.