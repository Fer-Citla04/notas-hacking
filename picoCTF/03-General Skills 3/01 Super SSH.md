## **Reto**:1 -> Super SSH

## **Descripción**
Using a Secure Shell (SSH) is going to be pretty important.Can you `ssh` as `ctf-player` to `titan.picoctf.net` at port `52409` to get the flag?You'll also need the password `6dd28e9b`. If asked, accept the fingerprint with `yes`.If your device doesn't have a shell, you can use: [https://webshell.picoctf.org](https://webshell.picoctf.org/)If you're not sure what a shell is, check out our Primer: [https://primer.picoctf.com/#_the_shell](https://primer.picoctf.com/#_the_shell)

## **Solución**
Primero entré a la terminal y puse este comando:
`ssh ctf-player@titan.picoctf.net -p 52409`
para entrar a un servidor remoto.

Al momento de pedirme la contraseña, puse la sig:
`6dd28e9b`

Una vez dentro, el mismo sistema me mostró la bandera
```
picoCTF{s3cur3_c0nn3ct10n_5d09a462}
```

