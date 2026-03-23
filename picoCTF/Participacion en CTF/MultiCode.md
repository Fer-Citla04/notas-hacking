## **Descripción**
El reto consiste en interceptar y decodificar un mensaje que ha sido ocultado mediante múltiples capas de obcecación no cifrada. El objetivo es identificar los métodos de codificación comunes y revertirlos en el orden correcto para extraer el flag final. 

**Mensaje inicial:** NjM3NjcwNjI1MDQ3NTMyNTM3NDI2MTcyNjY2NzcyNzE1Zjc3N2U2MTcyMDMwNzE3NjYxNzQ1ZjczNzM2ZjM2NzA2ZTZlMzIyNTM3NDQ=
## **Solución**
Para resolver este reto, se utilizó la herramienta **CyberChef** siguiendo un proceso de "desenvolvimiento" de afuera hacia adentro. El orden de las capas identificado fue: 

1. **From Base64**: Convierte la cadena original en una cadena hexadecimal. 
2. **From Hex**: Traduce los valores hexadecimales a texto ASCII (mostrando el flag obsecado). 
3. **URL Decode**: Limpia los códigos de porcentaje para mostrar las llaves { }. 
4. **ROT13 (Amount 13)**: Revela el texto final en texto claro. 

```
picoCTF{nested_enc0ding_ffb6caa2}
```

## **Notas adicionales
- **Importancia del Orden:** En este reto, el orden de las operaciones es crítico. Si se aplica **ROT13** antes de **URL Decode**, los caracteres hexadecimales del código URL (como la B en %7B) rotan a una O (%7O), lo que impide que la herramienta reconozca el símbolo correctamente.
## **Referencias
[https://toolbox.itsec.tamu.edu/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)From_Hex('Auto')ROT13(true,true,false,13)&input=TmpNM05qY3dOakkxTURRM05UTXlOVE0zTkRJMk1UY3lOalkyTnpjeU56RTFaamN5TmpFM01ETXdOekUzTmpZeE56UTFaamN6TnpNMlpqTTJOekEyWlRabE16SXlOVE0zTkRR](https://toolbox.itsec.tamu.edu/#recipe=From_Base64\('A-Za-z0-9%2B/%3D',true,false\)From_Hex\('Auto'\)ROT13\(true,true,false,13\)&input=TmpNM05qY3dOakkxTURRM05UTXlOVE0zTkRJMk1UY3lOalkyTnpjeU56RTFaamN5TmpFM01ETXdOekUzTmpZeE56UTFaamN6TnpNMlpqTTJOekEyWlRabE16SXlOVE0zTkRR)