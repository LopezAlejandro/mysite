+++
title= "Recuperar Nombre De Archivos en TikiWiki"
date= 2019-11-19T14:06:00-03:00
tags= ["documentacion"]
+++

### Recuperar el nombre original de los archivos en TikiWiki
```bash
mysql --host=localhost --user=dbuser --password=secret -D dbname\
      -B --raw <<<'select f.path, g.name, f.filename from tiki_files f, tiki_file_galleries g where f.galleryId = g.galleryId'\
       | sed "s:^:install -D files/:;s:\t: 'export/:;s:\t:/:;s:$:':" | sh
``` 
