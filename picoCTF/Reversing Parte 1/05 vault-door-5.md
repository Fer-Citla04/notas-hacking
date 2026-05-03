## **Reto**:  vault-door-5
## **Descripción**
In the last challenge, you mastered octal (base 8), decimal (base 10), and hexadecimal (base 16) numbers, but this vault door uses a different change of base as well as URL encoding!The source code for this vault is here: [VaultDoor5.java](https://challenge-files.picoctf.net/c_fickle_tempest/aee691634d8cfd4a10820634bdea6b80aa104301e4b83d01fd4d176098d69e99/VaultDoor5.java)

## **Solución**

1. El primer paso consistió en leer el archivo `VaultDoor5.java` con el comando cat y lo que apareció fue lo siguiente:
   `──(kali㉿kali)-[~/Documentos/vault-door-5]`
`└─$ cat VaultDoor5.java`  
`import java.net.URLDecoder;`
`import java.util.*;`

`class VaultDoor5 {`
    `public static void main(String args[]) {`
        `VaultDoor5 vaultDoor = new VaultDoor5();`
        `Scanner scanner = new Scanner(System.in);`
        `System.out.print("Enter vault password: ");`
        `String userInput = scanner.next();`
        `String input = userInput.substring("picoCTF{".length(),userInput.length()-1);`
        `if (vaultDoor.checkPassword(input)) {`
            `System.out.println("Access granted.");`
        `} else {`
            `System.out.println("Access denied!");`
        `}`
    `}`

    // Minion #7781 used base 8 and base 16, but this is base 64, which is
    // like... eight times stronger, right? Riiigghtt? Well that's what my twin
    // brother Minion #2415 says, anyway.
    //
    // -Minion #2414
    public String base64Encode(byte[] input) {
        return Base64.getEncoder().encodeToString(input);
    }

    // URL encoding is meant for web pages, so any double agent spies who steal
    // our source code will think this is a web site or something, defintely not
    // vault door! Oh wait, should I have not said that in a source code
    // comment?
    //
    // -Minion #2415
    public String urlEncode(byte[] input) {
        StringBuffer buf = new StringBuffer();
        for (int i=0; i<input.length; i++) {
            buf.append(String.format("%%%2x", input[i]));
        }
        return buf.toString();
    }

    public boolean checkPassword(String password) {
        String urlEncoded = urlEncode(password.getBytes());
        String base64Encoded = base64Encode(urlEncoded.getBytes());
        String expected = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVm"
                        + "JTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2"
                        + "JTM0JTVmJTY1JTY0JTMwJTYyJTM0JTMyJTM4JTM4";
        return base64Encoded.equals(expected);
    }
}                
2. Para obtener la contraseña original, se debe aplicar el proceso inverso en el orden contrario:
   -  **Decodificar de Base64** para obtener la cadena con formato URL.
   - **Decodificar de URL** para obtener el texto plano de la bandera.
 
 3. Ejecuté el comando:

    `echo "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVmJTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2JTM0JTVmJTY1JTY0JTMwJTYyJTM0JTMyJTM4JTM4" | base64 -d | python3 -c "import sys, urllib.parse; print(urllib.parse.unquote(sys.stdin.read()))"`

4. La ejecución del comando anterior devolvió la cadena limpia: `c0nv3rt1ng_fr0m_ba5e_64_ed0b4288`

```
picoCTF{c0nv3rt1ng_fr0m_ba5e_64_ed0b4288}
```
## **Notas adicionales
- **`urlEncode`**: Convierte los caracteres de la contraseña a formato de codificación URL (por ejemplo, el carácter `c` se convierte en `%63`).
- **`base64Encode`**: Toma la cadena codificada por URL y la convierte a **Base64**.
- **`echo "..."`**: Introduce la cadena codificada al pipeline.
- **`base64 -d`**: Realiza la decodificación de Base64. Esto genera una cadena intermedia llena de símbolos `%` (ej. `%63%30%6e...`).
- **`python3 -c "..."`**: Utiliza el módulo `urllib.parse` de Python para ejecutar la función `unquote`, que traduce los códigos hexadecimales de URL a caracteres ASCII legibles.