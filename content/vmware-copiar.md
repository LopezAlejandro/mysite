+++
title= "Copiar una VM de un servidor ESXi a otro"
date= 2020-08-27T16:07:20-03:00

[taxonomies]
categories = ["Virtualizacion"]
tags = ["documentacion", "vmware"]
authors = ["Alejandro Lopez"]
+++


## Copiar un VM de un servidor ESXi a otro

### Usando SCP

         scp usuario@origen:/path/a/copiar  usuario@destino:/path/de/destino/

### Usando NC

Aparentemente vmware ralentiza las operaciones de ssh, para eso usamos netcat

- En el destino ponemos :

            nc -vl 6969 | tar zxv

- En el origen hacemos :

            tar czp /path/a/copiar/ | nc -N ip.des.ti.no 6969

Para evitar que se interrumpa el comando, podemos agregar nohup delante de cada uno.