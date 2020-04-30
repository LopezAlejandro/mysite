+++
title= "Mail Consola"
date= 2019-10-08T14:18:32-03:00
tags= ["mail","consola"]
+++

Para enviar un mail por consola a traves de gmail , tenemos que usar el programa mailx.

Con el script siguiente podemos enviar un mail con un attach a una lista de receptores.

```bash
#!/bin/sh
# servidor de salida
FROM_EMAIL_ADDRESS="enviador@mi-dominio.com"
FRIENDLY_NAME="nombre-humano"
EMAIL_ACCOUNT_PASSWORD="contraseña"
SERVER_SMTP="smtp://smtp.gmail.com:587"
EMAIL_SUBJECT="Lo que quieras como subject"

while IFS=, read -r TO_EMAIL_ADDRESS FILE_ATTACH
do
    # todo lo que pongamos en el echo, sera el contenido del correo
    echo "Cualquier cosa que quieras poner.
    " | mailx -v -s "$EMAIL_SUBJECT" \
    -a $FILE_ATTACH \
    -S smtp-use-starttls \
    -S ssl-verify=ignore \
    -S smtp-auth=login \
    -S smtp=$SERVER_SMTP \
    -S from="$FROM_EMAIL_ADDRESS($FRIENDLY_NAME)" \
    -S smtp-auth-user=$FROM_EMAIL_ADDRESS \
    -S smtp-auth-password=$EMAIL_ACCOUNT_PASSWORD \
    $TO_EMAIL_ADDRESS
done < listado.txt
```


El formato de listado.txt es el siguiente :

receptor1,nombre de archivo1

receptor2,nombre de archivo2
