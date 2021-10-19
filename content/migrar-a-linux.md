+++
title= "Migrar bases cd/isis de windows a linux"
date= 2019-11-19T11:59:56-03:00
tags= ["documentacion","cd/isis","linux","windows"]
+++
### Como migrar uns base cd/isis en windows a linux

Esto lleva varios pasos a saber :

1. Desde windows pasamos la base a modo texto :<br>
	**i2di BASE > BASE.TXT**

2. Se copia el archivo de texto a linux.

3. Desde la terminal de linux pasamos la codificacion del texto CP850 a MS-ANSI.\
Esto elimina los caracteres extraños.<br>
	**iconv -f CP850 -t MS-ANSI BASE.TXT -o BASE1.TXT**
	
4. Con el archivo generado, creamos una base nueva<br>
	**id21 BASE1.TXT create=BASE**

5. Regeneramos el indice y reinvertimos<br>
	**mx BASE fst=@BASE.FST fullinv/ansi = BASE -all now tell=10**
	
Con esto tenemos convertida la base.	
 		



