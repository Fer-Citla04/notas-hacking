## **Reto**:  vault-door-4
## **Descripción**
This vault uses ASCII encoding for the password.The source code for this vault is here: [VaultDoor4.java](https://challenge-files.picoctf.net/c_fickle_tempest/5a242afc9022df976b1c18fe9364788579431217536fca41006714b29d8931e1/VaultDoor4.java)
## **Solución**
1. El primer paso es inspeccionar el archivo descargado para identificar los valores que conforman la contraseña`cat VaultDoor4.java.1`
2. Para reconstruir la bandera, es necesario convertir cada byte a su representación de texto. Dado que realizar esto manualmente con una tabla ASCII es lento y propenso a errores, lo ideal es usar un script.

 Valores identificados en el código:
- **Decimales:** `106, 85, 53, 116, 95, 52, 95, 98`
- **Hexadecimales:** `0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f`
- **Octales:** `0142, 0131, 0164, 063, 0163, 0137, 040, 063`
- **Caracteres:** `'0', 'd', 'c', '8', '5', 'b', 'e', 'd'`

3. Ejecuté el comando

`python3 -c "`
`myBytes = [`
    `106 , 85  , 53  , 116 , 95  , 52  , 95  , 98  ,`
    `0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,`
    `0o142, 0o131, 0o164, 0o63, 0o163, 0o137, 0o40, 0o63,`
    `'0', 'd', 'c', '8', '5', 'b', 'e', 'd'`
`]`
`flag = ''.join([chr(b) if isinstance(b, int) else b for b in myBytes])`
`print('picoCTF{' + flag + '}')`
`"`

4. Al procesar los datos, la cadena resultante se divide así:

- **Segmento 1 (Decimal):** `jU5t_4_b`
- **Segmento 2 (Hex):** `UnCh_0f_`
- **Segmento 3 (Octal):** `byt3s_ 3` (El `040` es un espacio)
- **Segmento 4 (Char):** `0dc85bed`


```
picoCTF{jU5t_4_bUnCh_0f_byt3s_ 30dc85bed}
```
