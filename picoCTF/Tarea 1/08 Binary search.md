## **Reto**: Binary search

## **Descripción**
Want to play a game? As you use more of the shell, you might be interested in how they work! Binary search is a classic algorithm used to quickly find an item in a sorted list. Can you find the flag? You'll have 1000 possibilities and only 10 guesses. Cyber security often has a huge amount of data to look through - from logs, vulnerability reports, and forensics. Practicing the fundamentals manually might help you in the future when you have to write your own tools! You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_atlas/6/challenge.zip)

`ssh -p 60393 ctf-player@atlas.picoctf.net` Using the password `6dd28e9b`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!

## **Solución**
1. Primero, abrí la terminal en Kali y me conecté al servidor mediante SSH con el comando `ssh -p 60393 ctf-player@atlas.picoctf.net`.
2. Al entrar, al instante el juego comenzó pidiendo adivinar un número entre 1 y 1000.
3. Para descubrir el numero, primero
    - Empecé con **500** (mitad de 1000) -> El sistema dijo: "Higher" 
    - Probé **600** -> Dijo: "Lower" (Más bajo).
    - Fui ajustando el rango: **550**, **560**, **570**, **580**... hasta que el rango se hizo muy pequeño entre 580 y 590.
`┌──(kali㉿kali)-[~]`
`└─$ ssh -p 60393 ctf-player@atlas.picoctf.net`
`** WARNING: connection is not using a post-quantum key exchange algorithm.`
`** This session may be vulnerable to "store now, decrypt later" attacks.`
`** The server may need to be upgraded. See https://openssh.com/pq.html`
`ctf-player@atlas.picoctf.net's password:` 
`Welcome to the Binary Search Game!`
`I'm thinking of a number between 1 and 1000.`
`Enter your guess: 500`
`Higher! Try again.`
`Enter your guess: 600`
`Lower! Try again.`
`Enter your guess: 550`
`Higher! Try again.`
`Enter your guess: 560`
`Higher! Try again.`
`Enter your guess: 570`
`Higher! Try again.`
`Enter your guess: 580`
`Higher! Try again.`
`Enter your guess: 590`
`Lower! Try again.`
`Enter your guess: 585`
`Higher! Try again.`
`Enter your guess: 587`
`Congratulations! You guessed the correct number: 587`
`Here's your flag: picoCTF{g00d_gu355_de9570b0}`
`Connection to atlas.picoctf.net closed`

4. Finalmente, probé con el número **587**, y era el correcto.
5. Así fue como conseguí la bandera de este reto

```
picoCTF{g00d_gu355_de9570b0}
```

