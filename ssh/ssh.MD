- Copy folder

```
tar cf - dir | gzip -3 | ssh remotehost '
  cd /path/on/remote && gunzip | tar xf -'
```

- Copy folder and put the output directory

```
 tar cf - inputdir | gzip -3 | ssh remotehost '
  cd /path/on/remote && mkdir outputfolder && gunzip | tar xf - -C outputfolder --strip-components=1'
```

