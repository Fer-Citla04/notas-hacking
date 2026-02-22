## **Reto**: 3 -> Wave a flag

## **Descripción**
Can you invoke help flags for a tool or binary? This program has extraordinarily helpful information... [warm](https://challenge-files.picoctf.net/c_wily_courier/11d04620d1b8e59680f745f5e3d3957d48628b1e3e7c56c74c0030e82a778d63/warm)

## **Solución**
Primero descargo el archivo que me da.
Luego en la terminal pongo el comando file para verificar si se puede ejecutar.
Al ejecutarlo con ./warm me daba un error debido a los permisos de ejecución y para solucionar esto lo hice con el comando `chmod +x warm`
Lo volví a ejecutar ./warm -h y asi fue como obtuve la bandera de este reto.

```
picoCTF{b1scu1ts_4nd_gr4vy_ac5832c}
```

## **Notas adicionales**
El -h se utiliza en este caso para mostrar las funciones ocultas del archivo, pero es para pedir ayuda.
 rm -rf * : Se utiliza para eliminar un archivo desde la terminal de picoCTF.
Fernanda_Floress-picoctf@webshell:~$ wget https://challenge-files.picoctf.net/c_wily_courier/11d04620d1b8e59680f745f5e3d3957d48628b1e3e7c56c74c0030e82a778d63/warm
--2026-02-11 18:37:32--  https://challenge-files.picoctf.net/c_wily_courier/11d04620d1b8e59680f745f5e3d3957d48628b1e3e7c56c74c0030e82a778d63/warm
el wget para descargar.
