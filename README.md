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

## Installation

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

## Upload test data into DB

Copy db file from your app directory into container using next command:
```sh
$ docker cp <DB FILE> <CONTAINER>:/app/<DATABASE>
```
Load data from file inside your container:
```sh
$ docker container exec -it <CONTAINER> bash
```
```
python manage.py loaddata <DATABASE>
```

## Made by Mikhail Rizhikau, Alexey Nikolaev, Artem Sinitsyn. Curated by Ya.Practicum.