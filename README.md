
# pymongo-api

## Схемы для задания 1, 5, 6
https://drive.google.com/file/d/1RU6AOmH-qBJAdR2rnlsOPsjmPKX86vxK/view?usp=sharing

## Как запустить

Запускаем mongodb и приложение

```shell
docker compose up -d
```

Заполняем mongodb данными

```shell
./scripts/mongo-init.sh
```

## Как проверить

### Проверка шардирования

У нас 2 набора реплик:
- shard1
	+ shard1-n1
	+ shard1-n2
	+ shard1-n3
- shard2
	+ shard2-n1
	+ shard2-n2
	+ shard2-n3

Было создано 5000 документов.

Осуществить проверку и вывести количество документов в каждом из шардов, количество реплик можно запустив скрипт:

```shell
./scripts/test.sh
```

### Проверка кеширования

Запустите несколько раз команду:
```shell
time curl http://localhost:8080/helloDoc/users
```
Второй и последующие вызовы эндпоинта /<collection_name>/users выполняются быстрее.
