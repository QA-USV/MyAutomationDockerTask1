# Домашнее задание к занятию «Docker»

## Задача: PostgreSQL

Необходимо подготовить приложение к тестированию на СУБД PostgreSQL. Используйте образ 12-alpine, если он недоступен, то берите последний опубликованный на Docker Hub. Возьмите собранный JAR-файл `db-api.jar`, аналогично примеру на лекции положите рядом файл `application.properties`, но в строке:
`jdbc:mysql://...` поменяйте `mysql` на `postgresql`.

Необходимо дописать остальные настройки: хост, порт, БД, имя пользователя и пароль.         

Необходимо подготовить файл `docker-compose.yml`, в котором прописать настройки для запуска контейнера PostgreSQL. Всю информацию о его запуске вы найдёте на официальной странице [образа на Docker Hub](https://hub.docker.com/_/postgres). Рекомендуем также изучить документацию по [СУБД PostgreSQL](https://www.postgresql.org/docs/12/index.html) для получения информации о данном продукте. 

Запустить сначала `docker-compose up` и только после того, как БД запустится, запустить целевое приложение: `java -jar db-api.jar`. Если нужно поменять порт запуска, по умолчанию он 9999, то добавьте в файл `application.properties` строку `server.port=<нужный номер порта>`.

Если сделали всё правильно, то приложение запустится и на `GET http://localhost:9999/api/cards` выдаст вам JSON с картами:
```json
[ 
   { 
      "id":1,
      "name":"Альфа-Карта Premium",
      "description":"Альфа-Карта вернёт ваши деньги",
      "imageUrl":"/alfa-card-premium.png"
   },
   { 
      "id":2,
      "name":"Alfa Travel Premium",
      "description":"Самая выгодная карта для путешествий",
      "imageUrl":"/alfa-card-travel.png"
   },
   { 
      "id":3,
      "name":"CashBack Premium",
      "description":"Заправь свою карту. Кешбэк на АЗС, в кафе и ресторанах",
      "imageUrl":"/alfa-card-cashback.png"
   }
]
```

В результате выполнения этой задачи вы должны положить в репозиторий следующие три файла (других файлов не должно быть):
* db-api.jar,
* application.properties,
* docker-compose.yml.
