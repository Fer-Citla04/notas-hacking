## **Reto**:  waves over lambda
## **Descripción**
We made a lot of substitutions to encrypt this. Can you decrypt it?Connect with nc fickle-tempest.picoctf.net 51039.

## **Solución**
1. Me conecté al servidor `nc fickle-tempest.picoctf.net 60213`
2. Lo que me dió fue lo siguiente:
kwqorafy thrh py vwcr szao - srhbchqkv_py_k_wuhr_zaigla_8003s343
-------------------------------------------------------------------------------
azhdhv svwlwrwupfkt naraiamwu jay fth ftprl ywq ws svwlwr eauzwupfkt naraiamwu, a zaql wjqhr jhzz nqwjq pq wcr lpyfrpkf pq tpy wjq lav, aql yfpzz rhihighrhl aiwqo cy wjpqo fw tpy ozwwiv aql fraopk lhaft, jtpkt taeehqhl ftprfhhq vhary aow, aql jtpkt p ytazz lhykrpgh pq pfy erwehr ezakh. swr fth erhyhqf p jpzz wqzv yav ftaf ftpy zaqlwjqhrswr yw jh cyhl fw kazz tpi, azftwcot th tarlzv yehqf a lav ws tpy zpsh wq tpy wjq hyfafhjay a yfraqoh fveh, vhf wqh erhffv srhbchqfzv fw gh ihf jpft, a fveh agxhkf aql upkpwcy aql af fth yaih fpih yhqyhzhyy. gcf th jay wqh ws ftwyh yhqyhzhyy ehrywqy jtw arh uhrv jhzz kaeagzh ws zwwnpqo asfhr fthpr jwrzlzv assapry, aql, aeearhqfzv, asfhr qwftpqo hzyh. svwlwr eauzwupfkt, swr pqyfaqkh, ghoaq jpft qhdf fw qwftpqo; tpy hyfafh jay ws fth yiazzhyf; th raq fw lpqh af wfthr ihq'y fagzhy, aql sayfhqhl wq fthi ay a fwalv, vhf af tpy lhaft pf aeeharhl ftaf th tal a tcqlrhl ftwcyaql rwcgzhy pq tarl kayt. af fth yaih fpih, th jay azz tpy zpsh wqh ws fth iwyf yhqyhzhyy, saqfayfpkaz shzzwjy pq fth jtwzh lpyfrpkf. p rhehaf, pf jay qwf yfceplpfvfth iaxwrpfv ws fthyh saqfayfpkaz shzzwjy arh ytrhjl aql pqfhzzpohqf hqwcotgcf xcyf yhqyhzhyyqhyy, aql a ehkczpar qafpwqaz swri ws pf.

3. utilicé **Guballa's Substitution Solver**. 
4. Al procesar el texto en la herramienta,  logró romper el cifrado.
Al inicio del texto decodificado, se presentó la frase de éxito junto con la bandera: `congrats here is your flag - frequency_is_c_over_lambda_8003f343`

Por último, extraje la bandera siguiendo las instrucciones del reto (que en este caso no utiliza las llaves clásicas de la competencia)
```
frequency_is_c_over_lambda_8003f343
```
## **Referencias
https://www.guballa.de/substitution-solver