### Docker ps 
``` sh
docker ps --format "table {{.ID}}\t{{.Names}}\t{{.Status}}\t{{.Ports}}"
```
### delete all containers including its volumes use
```sh
docker rm -v -f $(docker ps -qa)
```

### delete all the images
