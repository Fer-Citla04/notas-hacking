## **Reto**:  substitution1
## **Descripción**
A second message has come in the mail, and it seems almost identical to the first one. Maybe the same thing will work again.Download the message [here](https://artifacts.picoctf.net/c/183/message.txt).
## **Solución**
1. Descargué el archivo de la descripción con `wget`.
2. Ejecuté el message.txt con cat y apareció lo siguiente
                                                
┌──(kali㉿kali)-[~/Documentos/substitution1]
└─$ cat message.txt 
LKOb (bwvek ove lgqkhej kwj osgx) gej g kyqj vo lvrqhkje bjlhetky lvrqjktktvu. Lvukjbkgukb gej qejbjukjz dtkw g bjk vo lwgssjuxjb dwtlw kjbk kwjte lejgktftky, kjlwutlgs (guz xvvxstux) bitssb, guz qevmsjr-bvsftux gmtstky. Lwgssjuxjb hbhgssy lvfje g uhrmje vo lgkjxvetjb, guz dwju bvsfjz, jglw ytjszb g bketux (lgssjz g osgx) dwtlw tb bhmrtkkjz kv gu vustuj blvetux bjeftlj. LKOb gej g xejgk dgy kv sjgeu g dtzj geegy vo lvrqhkje bjlhetky bitssb tu g bgoj, sjxgs juftevurjuk, guz gej wvbkjz guz qsgyjz my rguy bjlhetky xevhqb gevhuz kwj dvesz ove ohu guz qeglktlj. Ove kwtb qevmsjr, kwj osgx tb: qtlvLKO{OE3AH3ULY_4774LI5_4E3_L001_6J0659OM}   

3. En la página quipqiup pegué el texto y me dió la bandera
   `CTFs (short for capture the flag) are a type of computer security competition. Contestants are presented with a set of challenges which test their creativity, technical (and googling) skills, and problem-solving ability. Challenges usually cover a number of categories, and when solved, each yields a string (called a flag) which is submitted to an online scoring service. CTFs are a great way to learn a wide array of computer security skills in a safe, legal environment, and are hosted and played by many security groups around the world for fun and practice. For this problem, the flag is: picoCTF{FR3QU3NCY_4774CK5_4R3_C001_6E0659FB}`

```
picoCTF{FR3QU3NCY_4774CK5_4R3_C001_6E0659FB}
```
## **Referencias**
https://quipqiup.com/