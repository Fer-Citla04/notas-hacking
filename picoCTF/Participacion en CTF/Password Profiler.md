## **Descripción**
We intercepted a suspicious file from a system, but instead of the password itself, it only contains its SHA-1 hash. Using OSINT techniques, you are provided with personal details about the target. Your task is to leverage this information to generate a custom password list and recover the original password by matching its hash. Download the following files: userinfo: Contains the personal details. hash: Contains the SHA-1 hash of the password. check_password: Script to test passwords against the hash

## **Solución**

CUPP is a Python tool for generating custom wordlists from personal data.

┌──(kali㉿kali)-[~/Downloads/Concurso/PasswordProfiler/cupp]  
└─$ python3 cupp.py -i  
 _**_**_**__  
   cupp.py! # Common  
      \ # User  
       \ ,_*, # Passwords  
        \ (oo)_*** # Profiler  
           (__) )\  
              ||--|| * [ Muris Kurgas | j0rgan@remote-exploit.org ]  
                            [ Mebus | [https://github.com/Mebus/\](https://github.com/Mebus/%5C)]



[+] Insert the information about the victim to make a dictionary  
[+] If you don't know all the info, just hit enter when asked! ;)

> First Name: Alice  
> Surname: Johnson  
> Nickname: AJ  
> Birthdate (DDMMYYYY): 15071990



> Partners) name: Bob  
> Partners) nickname: Bob  
> Partners) birthdate (DDMMYYYY): 15071990



> Child's name: Charlie  
> Child's nickname: Charlie  
> Child's birthdate (DDMMYYYY): 15071990



> Pet's name: a  
> Company name: a



> Do you want to add some key words about the victim? Y/[N]: n  
> Do you want to add special chars at the end of words? Y/[N]: y  
> Do you want to add some random numbers at the end of words? Y/[N]:y  
> Leet mode? (i.e. leet = 1337) Y/[N]: y

[+] Now making a dictionary...  
[+] Sorting list and removing duplicates...  
[+] Saving dictionary to alice.txt, counting 33146 words.  
> Hyperspeed Print? (Y/n) : n  
[+] Now load your pistolero with alice.txt and shoot! Good luck!

┌──(kali㉿kali)-[~/Downloads/Concurso/PasswordProfiler/cupp]  
└─$ mv Alice.txt ~/Downloads/Concurso/PasswordProfiler/passwords.txt  
mv: cannot stat 'Alice.txt': No such file or directory

┌──(kali㉿kali)-[~/Downloads/Concurso/PasswordProfiler/cupp]  
└─$ ls  
alice.txt cupp.cfg LICENSE screenshots  
CHANGELOG.md cupp.py README.md test_cupp.py

┌──(kali㉿kali)-[~/Downloads/Concurso/PasswordProfiler/cupp]  
└─$ mv alice.txt ~/Downloads/Concurso/PasswordProfiler/passwords.txt

┌──(kali㉿kali)-[~/Downloads/Concurso/PasswordProfiler/cupp]  
└─$ cd ~/Downloads/Concurso/PasswordProfiler  
python3 check_password.py  
Password found: picoCTF{Aj_15901990}

┌──(kali㉿kali)-[~/Downloads/Concurso/PasswordProfiler]

```
picoCTF{Aj_15901990}
```
