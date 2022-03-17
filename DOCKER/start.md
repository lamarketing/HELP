### Образ из реестра(registry)
`docker pull postgres:13.0-alpine `

— скачивает образ из реестра.
В примере будет скачан образ СУБД PostgreSQL 13 на базе ОС Alpine.

`docker push some_registry.com/image_name:image_version `

— сохраняет образ в реестре.

`docker run postgres:13.0-alpine` 

— запускает контейнер. 
Если указанного образа нет, то образ скачается, 
как в команде docker pull.

### СОЗДАНИЕ ОБРАЗА
`docker build` 
собирает новый образ(image) из кода. Нужен Dockerfile

`docker create `
creates a writeable container from the image and prepares it for running.

`docker run` 
creates the container (same as docker create) and runs it.

### Dockerfile
```
# Указываем образ, от которого берётся наследование
FROM ubuntu:18.04

# Обновляем индекс пакетов
RUN apt update -y
# Устанавливаем интерпретатор
RUN apt install -y python3

# Указываем команду, которая должна выполниться 
при старте контейнера
CMD ["python3"]
```
Название может быть любым, например: Dockerfile_base

В этом случае:

`docker build -f Dockerfile_base -t my_python_base_image .`

-f - file, название файла, из которого строить image(образ)

-t - tag, название будущего образа

точка - контекст сборки

###