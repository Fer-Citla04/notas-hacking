## **Reto**: 2 -> Runme.py

## **Descripción**
Run the `runme.py` script to get the flag. Download the script with your browser or with `wget` in the webshell.[Download runme.py Python script](https://artifacts.picoctf.net/c/34/runme.py)
## **Solución**
- Lo primero a hacer es descargar el script de Python desde el servidor de picoCTF, por lo tanto se utiliza el comando wget
`wget` https://artifacts.picoctf.net/c/34/runme.py

- Luego, se verifica si el archivo ya está descargado con ls.
- Una vez asegurado, como es un archivo de Python, se necesita el intérprete de Python para "leerlo" y ejecutar las instrucciones que tiene dentro (ejecutamos el archivo de python) con el comando:
`python3 runme.py`
- Y así es como en este reto se obtuvo la bandera.
```
picoCTF{run_s4n1ty_run}
```

