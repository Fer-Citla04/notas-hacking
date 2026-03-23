## **Descripción**
 Can you conjure the right bytes? The program's source code can be downloaded here and the compiled spellbook binary can be downloaded here. Connect to the program with netcat: $ nc green-hill.picoctf.net 63022

## **Solución**
┌──(kali㉿kali)-[~/…/Concurso/MYGIT/challenge/bytemancy3]  
└─$ nm spellbook | grep -E 'ember_sigil|glyph_conflux|astral_spark|binding_word'  
080491c1 T astral_spark  
080491e3 T binding_word  
08049176 T ember_sigil  
0804919a T glyph_conflux

┌──(kali㉿kali)-[~/…/Concurso/MYGIT/challenge/bytemancy3]  
└─$ nvim solve.py

┌──(kali㉿kali)-[~/…/Concurso/MYGIT/challenge/bytemancy3]  
└─$ python3 solve.py  
[*] '/home/kali/Downloads/Concurso/MYGIT/challenge/bytemancy3/spellbook'  
    Arch: i386-32-little  
    RELRO: No RELRO  
    Stack: No canary found  
    NX: NX unknown - GNU_STACK missing  
    PIE: No PIE (0x8048000)  
    Stack: Executable  
    RWX: Has RWX segments  
    SHSTK: Enabled  
    IBT: Enabled  
    Stripped: No  
    Debuginfo: Yes  
[x] Opening connection to green-hill.picoctf.net on[O] Opening connection to green-hill.picoctf.net on[0] Opening connection to green-hill.picoctf.net on[+] t 63022: Done  
[*] Enviando dirección de binding_word: 0x80491e3  
[*] Enviando dirección de ember_sigil: 0x8049176  
[*] Enviando dirección de astral_spark: 0x80491c1  
[*] Switching to interactive mode  
.  
==> picoCTF{0bjdump_m4g1c_bb59765a}  
[*] Got EOF while reading in interactive  
$  
[*] Interrupted  
[*] Closed connection to green-hill.picoctf.net port 63022

┌──(kali㉿kali)-[~/…/Concurso/MYGIT/challenge/bytemancy3]  
└─$

```
picoCTF{0bjdump_m4g1c_bb59765a} 
```