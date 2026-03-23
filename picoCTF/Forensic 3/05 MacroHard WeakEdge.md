## **Reto**:  MacroHard WeakEdge
## **Descripción**
I've hidden a flag in this file. Can you find it?[Forensics_is_fun.pptm](https://challenge-files.picoctf.net/c_wily_courier/d78815176c19ddc85a1388233268d2f4c459fcbbaab197b4a29ebafc88294c54/Forensics_is_fun.pptm)
## **Solución**
Primero, descargué el archivo, vi que tenía la extensión `.pptm`. 
Para resolver este reto, seguí estos pasos:

1. Descomprimir el archivo: Utilicé el comando `unzip` para extraer todo el contenido del archivo de PowerPoint: `unzip Forensics_is_fun.pptm -d macro_content`

2. Entré a la carpeta creada y empecé a navegar por la estructura XML. Intenté buscar la palabra "pico" en todos los archivos con `grep -r "pico"`, pero no obtuve resultados. 

3. Al explorar las carpetas más a fondo, encontré un archivo con nombre llamado **`hidden`**.

4. Al abrir el archivo `hidden`, encontré una cadena de texto larga que parecía estar codificada en **Base64** 

5. Copié la cadena y, como tenía espacios que podían arruinar la conversión, usé el comando `tr` para limpiarla y luego `base64` para traducirla: `cat hidden | tr -d ' ' | base64 -d`


Al ejecutar el comando, la terminal me devolvió la bandera :
```
picoCTF{D1d_u_kn0w_ppts_r_z1p5}
```

## **Referencias
https://www.youtube.com/watch?v=CsCeOp9PFGs&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=28