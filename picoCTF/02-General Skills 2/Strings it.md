## **Reto**: 2-> Strings it

## **Descripción**
Can you find the flag in [file](https://challenge-files.picoctf.net/c_fickle_tempest/fd00e7cc9b263f22c323572d2d5fc37d170f8e58e99a91f8991d0f07c69b21ff/strings) without running it?

## **Solución**
Existen varias formas de resolverlo y para mi la más sencilla es descargar el archivo, abrirlo en bloc de notas y con control p busco la palabra picoCTF y busca el resultado.
```
picoCTF{5tRIng5_1T_FB7D7Bb6}
```

## **Notas adicionales**
Otra forma de resolverlo es descargarlo y desde la terminal poner el comando
`strings strings | grep "picoCTF"`

