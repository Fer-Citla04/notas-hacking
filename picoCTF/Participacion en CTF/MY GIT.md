## **Descripción**
I have built my own Git server with my own rules! You can clone the challenge repo using the command below. git clone ssh://git@foggy-cliff.picoctf.net:51177/git/challenge.git Here's the password: e38a0906 Check the README to get your flag!
How do you specify your Git username and email?
## **Solución**
git clone ssh://git@foggy-cliff.picoctf.net:51177/git/challenge.git  
cd challenge

git config user.name "root"  
git config user.email "root@picoctf"

echo "peticion de flag" > flag.txt

git add flag.txt  
git commit -m "Give me the flag"

git push origin master

**`picoCTF{1mp3rs0n4t4_g17_345y_02a39618}`**

