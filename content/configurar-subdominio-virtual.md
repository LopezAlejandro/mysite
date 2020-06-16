+++
title= "Configurar subdominio en un DNS"
date= 2020-05-18T15:42:00-03:00

[taxonomies]
categories = ["dns"]
tags = ["subdominios", "mail"]
authors = ["Alejandro Lopez"]
+++

### Crear un subdominio virtual

En este caso suponemos de tenemos configurado un servidor DNS donde hemos configurado la zona example.org en el fichero */var/cache/bind/db.example.org.* La configuración del subdominio virtual se ha indicado en negrita, y quedaría de la siguiente manera:
```bash	
	$TTL    86400
	@       IN      SOA     ns1.example.org. mail.example.org. (
	                              4         
	                         604800         
	                          86400         
	                        2419200       
	                          86400 )       
		
	$ORIGIN example.org.
	@       IN      NS      ns1
		
	ns1     IN      A       10.0.10.2
	www     IN      A       10.0.10.1
		
	$ORIGIN es.example.org.
	www     IN      A      10.10.0.3
```

Después de reiniciar el servidor podemos hacer una consulta con la utilidad dig, de la siguiente manera:


$ dig @10.0.10.2 www.es.example.org
```bash
	; <<<<>>>> DiG 9.8.4-rpz2+rl005.12-P1 <<<<>>>> @10.0.10.2 www.es.example.org
	; (1 server found)
	;; global options: +cmd
	;; Got answer:
	;; ->>>>HEADER<<<<- opcode: QUERY, status: NOERROR, id: 61235
	;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1
	
	;; QUESTION SECTION:
	;www.es.example.org.		IN	A
	
	;; ANSWER SECTION:
	www.es.example.org.	86400	IN	A	10.10.0.3
	
	;; AUTHORITY SECTION:
	example.org.		86400	IN	NS	ns1.example.org.
	
	;; ADDITIONAL SECTION:
	ns1.example.org.	86400	IN	A	10.0.10.2
	
	;; Query time: 0 msec
	;; SERVER: 10.0.10.2#53(10.0.10.2)
	;; WHEN: Thu Nov 21 15:27:26 2013
	;; MSG SIZE  rcvd: 86
```
Donde podemos observar que la resolución se hace correctamente, y como señalamos anteriormente el servidor con autoridad (registro NS) es el servidor *ns1.example.org* que, en realidad, es el servidor con autoridad del dominio example.org.