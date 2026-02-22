## **Reto**: 4°->Bases

## **Descripción**
What does this bDNhcm5fdGgzX3IwcDM1 mean? I think it has something to do with bases.

## **Solución**
En cyberchef pegué bDNhcm5fdGgzX3IwcDM1 from base64 y como resultado dió `l3arn_th3_r0p35`

Solución en python:
`import base64`
`s = "bDNhcm5fdGgzX3IwcDM1"`
`decoded = base64.b64decode(s).decode("utf-8")`
`print(decoded)`
`l3arn_th3_r0p35` 

```
picoCTF{`l3arn_th3_r0p35`}
```
## **Notas adicionales**
Esta herramienta (cyberchef) es muy útil para este tipo de soluciones.

## **Referencias**
https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)&input=YkROaGNtNWZkR2d6WDNJd2NETTE