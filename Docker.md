### Docker ps 
``` sh
docker ps --format "table {{.ID}}\t{{.Names}}\t{{.Status}}\t{{.Ports}}"
```
### delete all containers including its volumes use
```sh
docker rm -v -f $(docker ps -qa)
```

### delete all the images
```bash
docker rmi -f $(docker images -aq)
```
### Create an image
```bash
`docker build -t nextjs:latest -f Dockerfile .
```