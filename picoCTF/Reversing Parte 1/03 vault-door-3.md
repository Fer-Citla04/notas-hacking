## **Reto**:  vault-door-3
## **Descripción**
This vault uses for-loops and byte arrays.The source code for this vault is here: [VaultDoor3.java](https://challenge-files.picoctf.net/c_fickle_tempest/856cff883937e1cfe99e7e5b9c2fbbf08232a8135f919b1111615f007a4de03a/VaultDoor3.java)
## **Solución**
1. El primer paso fue leer el archivo `VaultDoor3.java` con cat para entender cómo se procesaba la entrada. 
   `cat VaultDoor3.java`
2. Se identificaron cuatro bloques de reordenamiento en el código Java:
   - **Índices 0-7:** Mapeo directo ($buffer[i] = s.charAt(i)$).
   - **Índices 8-15:** Mapeo invertido ($buffer[i] = s.charAt(23-i)$)
   - **Índices 16-31 (pasos de 2):** Mapeo calculado ($buffer[i] = s.charAt(46-i)$
   - **Índices 31-17 (pasos de -2):** Mapeo directo ($buffer[i] = s.charAt(i)$).
3. La cadena final con la que se comparaba el resultado:
   `"jU5t_a_sna_3lpm11g54e_u_4_m4r042"`
4. Para evitar errores manuales en el reordenamiento, se utilizó un "one-liner" de Python directamente en la terminal 
    
    `python3 -c '`
    `target = "jU5t_a_sna_3lpm11g54e_u_4_m4r042"`
    `password = [""] * 32`
    `for i in range(8): password[i] = target[i]`
    `for i in range(8, 16): password[23-i] = target[i]`
    `for i in range(16, 32, 2): password[46-i] = target[i]`
    `for i in range(31, 16, -2): password[i] = target[i]`
    `print("picoCTF{" + "".join(password) + "}")`
    `'`
    
```
picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_e45012}
```
