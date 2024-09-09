### Docker ps 
``` sh
docker ps --format "table {{.ID}}\t{{.Names}}\t{{.Status}}\t{{.Ports}}"
```
### Kill all containers and remove them
```sh
docker rm -v -f $(docker ps -qa)
```