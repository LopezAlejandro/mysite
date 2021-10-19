+++
title= "Comandos útiles de VMware"
date= 2020-08-28T10:32:20-03:00

[taxonomies]
categories = ["Virtualizacion"]
tags = ["documentacion", "vmware"]
authors = ["Alejandro Lopez"]
+++


## Agregar un disco a una VM

1. Hacer ssh al servidor :
		ssh root@IP del server

1. Buscar la ubicacion del datastore con el siguiente comando :
		esxcli storage filesystem list
		
1. Cambiar a ese directorio :
		cd Punto de montaje
		
1. Crear el disco con el siguiente comando :
		vmkfstools --createvirtualdisk XXXG --diskformat thin <nameYourDriveHere>.vmdk
	Donde XXX es el tamaño del disco
		
1. Agregar el disco en caliente  de la siguiente manera :
		vim-cmd vmsvc/getallvms
		
 	- Asi obtenemos el id de la maquina.
	- Ahora agregamos el disco :
	
		vim-cmd vmsvc/device.diskaddexisting <vmid> </vmfs/volumes/pathToDisk.vmdk> 0 1	
		
	- El 0 indica la placa SCSI y el 1 muestra los dispositivos conectados a la placa, el valor se va incrementando a medida que agregamos discos.	