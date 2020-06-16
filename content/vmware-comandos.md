+++
title= "Comandos útiles de VMware"
date= 2020-06-09T12:32:20-03:00

[taxonomies]
categories = ["Virtualizacion"]
tags = ["documentacion", "vmware"]
authors = ["Alejandro Lopez"]
+++


## ESXi SSH: comandos útiles de VMware CLI

|Comando |Descripción|
| :------------- | :----------: |
| **esxcfg-info** | Muestra información extendida del hardware del host ESXi|
| **esxtot** | Tiene prácticamente las mismas funcionalidades que el comando TOP de Linux|
| **vim-cmd hostsvc/maintenance_mode_enter**|Activa  el modo de mantenimento de un Host ESXi|
| **vim-cmd hostsvc/maintenance_mode_exit** |Deshabilita el modo de mantenimento de un Host ESXi|
| **vim-cmd vmsvc/getallvms**|Listado de máquinas virtuales|
| **vim-cmd vmsvc/power.on Vmid** | Arrancar máquina virtual|
| **vim-cmd vmsvc/power.off Vmid**| Parar máquina virtual|
| **vim-cmd vmsvc/power.reboot Vmid** | Reiniciar máquina virtual|
| **vim-cmd vmsvc/power.getstate Vmid** | Ver el estado de una máquina virtual|
| **vim-cmd vmsvc/get.summary Vmid** | Ver información y configuración de una máquina virtual|
| **vim-cmd vmsvc/destroy Vmid** | Borrar una máquina virtual|

