## **Reto**: Pixelated
## **Descripción**
I have these 2 images, can you make a flag out of them?[scrambled1.png](https://challenge-files.picoctf.net/c_wily_courier/e9637222852661fff9c7ef33644e4f2084ffe3c693d4efaad4d88eec98ddd3e4/scrambled1.png) [scrambled2.png](https://challenge-files.picoctf.net/c_wily_courier/e9637222852661fff9c7ef33644e4f2084ffe3c693d4efaad4d88eec98ddd3e4/scrambled2.png)
## **Solución**
1. El reto sugiere que la información de la bandera ha sido dividida en dos archivos  aleatorios. 
2.  Instalamos la librería Pillow de Python para la manipulación de píxeles: `pip install Pillow`
3. Hacemos un script diseñado para abrir ambos archivos y combinarlos. Utilizamos el método de mezcla (`blend`) con un valor de _alpha_ de 0.5, lo que genera una composición equilibrada de ambas fuentes de datos. 

`from PIL import Image` 

`def combine_images(image1_path, image2_path, output_path):` 
    `# Abrir las dos partes (scrambled1.png y scrambled2.png)`
    `image1 = Image.open(image1_path)` 
    `image2 = Image.open(image2_path)` 

    `# Verificar alineación de dimensiones`
    `if image1.size != image2.size:` 
        `raise ValueError("Las imágenes deben tener el mismo tamaño")` 

    `# Combinar simulando transparencia (superposición)`
    `combined_image = Image.blend(image1, image2, alpha=0.5)` 

    `# Guardar el resultado final`
    `combined_image.save(output_path)` 
    `print(f"Resultado generado en: {output_path}")`

`if __name__ == "__main__":` 
    `combine_images("scrambled1.png", "scrambled2.png", "combined_image.png")`

4. Al ejecutarlo se generó el archivo `combined_image.png`. Al abrir este archivo los patrones de ambas imágenes originales se complementaron, revelando el texto legible de la bandera. 

```
picoCTF{8CDF93C3}
```
## **Notas adicionales
- Pillow (PIL): Biblioteca potente que permite el acceso directo a los datos de los píxeles, facilitando operaciones matemáticas entre los valores RGB de distintas imágenes.