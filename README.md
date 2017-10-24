# manager.io
Dockerized http://manager.io accounting software version 17.10.52

Run with
```
docker run -v $(pwd)/data:/data -p 8080:8080 devishian/manager.io
```

Open your browser http://dockerhost:8080

Backup could be done by 
```
docker run --rm --volumes-from managerio_data_1 \
  -v $(pwd):/backup devishian/manager.io \
  tar czvf /backup/Manager-backup.tar.gz /data
```
Restore 
```
 docker run --rm --volumes-from managerio_data_1 \
  -v $(pwd):/backup \ 
 devishian/manager.io bash -c "cd / && tar xzvf /backup/Manager-backup.tar.gz"
 ```
 Where managerio_data_1 is your data container.
