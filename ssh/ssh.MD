- Copy folder

```
tar cf - dir | gzip -3 | ssh remotehost '
  cd /path/on/remote && gunzip | tar xf -'
```

