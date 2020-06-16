+++
title= "Como Subir El Sitio"
date= 2019-09-27T12:32:20-03:00

[taxonomies]
categories = ["web"]
tags = ["documentacion", "git"]
authors = ["Alejandro Lopez"]
+++

## Como subir el sitio a git

Para cada subida tenemos que hacer lo siguiente (después de hacer los cambios y probar en local):
```bash
zola build
```
```git
git add .
git commit -m "Mensaje"
git push origin master
```
