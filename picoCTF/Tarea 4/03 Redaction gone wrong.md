## **Reto**:  Redaction gone wrong
## **Descripción**
Now you DON’T see me.This [report](https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf) has some critical data in it, some of which have been redacted correctly, while some were not. Can you find an important key that was not redacted properly?

## **Solución**
1. Primero descargue el pdf 
2. Verifiqué las propiedades del archivo para asegurar que el sistema lo reconociera correctamente como un PDF.
    `pdftotext challenge.pdf -`

3. Utilicé la suite `poppler-utils`. La herramienta `pdftotext` procesa el flujo de objetos del PDF e ignora todas las instrucciones de renderizado gráfico `pdftotext challenge.pdf -`
4. Para agilizar la búsqueda, combiné la extracción con un filtro de búsqueda de patrones.
    `pdftotext challenge.pdf - | grep "picoCTF"`
Y asi consegui la bandera
```
picoCTF{C4n_Y0u_S33_m3_fully}
```
