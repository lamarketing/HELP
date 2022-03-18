### Удаление контейнера
```
$ docker ps -a
$ docker rm <id_container>
```
### Удаление вообще всех контейнеров
```
$ docker rm -v $(docker ps -aq)
```
### Удаление всех остановленных контейнеров
```
$ docker rm -v $(docker ps -aq -f status=exited)
```