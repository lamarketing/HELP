### Вход в контейнер
`docker-compose exec db sh`

db - имя сервиса в docker-compose.yaml
### Подключение к конкретной базе
`psql -U app movies_database `

далее

`CREATE SCHEMA content;`