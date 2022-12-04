# YaMDb

This is latest version of YaMDB review web-service. You can build a mobile or desktop app using this API.

### Tech stack

- Python
- Django
- Nginx
- Docker-compose

## .env pattern:

1.  settings.py:
```sh
# Secret key for setting.py
SECRET_KEY=default-key
# DB engine 
DB_ENGINE=django.db.backends.postgresql
# DB name
DB_NAME=postgres
# DB user login
POSTGRES_USER=login
# DB user password
POSTGRES_PASSWORD=password
# DB container name
DB_HOST=db
# DB port
DB_PORT=5432
```

### Installation

Для запуска приложения проделайте следующие шаги:

1. Clone repo.
2. Run ```$ sudo docker-compose up -d --build``` from */infra* folder to start docker-compose and build the container.
3. Get into Django app shell by ```$ sudo docker-compose exec web sh```
4. Set up Django app and collect statics by runing next commands from "web" shell:
```sh
python manage.py migrate
python manage.py createsuperuser
python manage.py collectstatic --no-input
```
5. Project is up. Admin panel is available at http:/localhost/admin, ReDoc is availiable at http:/localhost/redoc

## Загрузка тестовых значений в БД

Чтобы загрузить тестовые значения в базу данных перейдите в каталог проекта и скопируйте файл базы данных в контейнер приложения:
```
docker cp <DATA BASE> <CONTAINER ID>:/app/<DATA BASE>
```
Перейдите в контейнер приложения и загрузить данные в БД: 
```
docker container exec -it <CONTAINER ID> bash
python manage.py loaddata <DATA BASE>
```

## Made by Mikhail Rizhikau, Alexey Nikolaev, Artem Sinitsyn. Curated by Ya.Practicum.