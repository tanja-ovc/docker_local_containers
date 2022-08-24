# Docker YaMDB Local

### Проект YaMDB с инфраструктурой для локального деплоя

- Данный проект посвящен созданию инфраструктуры для __локального__ деплоя уже существующего проекта YaMDB (https://github.com/tanja-ovc/api_yamdb_group_project) с помощью Docker.

### Установка

Клонировать репозиторий и перейти в него в командной строке:

```https://github.com/tanja-ovc/docker_local_containers.git```

Убедиться, что находитесь в директории _docker_local_containers/_, либо перейти в неё:

```cd docker_local_containers/```

Cоздать и активировать виртуальное окружение:

```python3 -m venv venv```

```source venv/bin/activate```

При необходимости обновить pip:

```pip install --upgrade pip```

Установить зависимости из файла requirements.txt:

```cd api_yamdb```

```pip install -r requirements.txt```

### Запуск проекта

Для запуска контейнеров необходимо обращение к DockerHub и установленный Docker.

Загрузите образ проекта с DockerHub, выполнив команду ```docker pull tanjadocker/infra_yamdb:v1.17.12.21```, где ```v1.17.12.21``` - номер версии проекта.

Перейдите в директорию _infra/_, где находится файл docker-compose. Соберите контейнеры:

```docker-compose up```

Выполните по очереди команды (выполнить миграции, создать суперпользователя и собрать статику):

```docker-compose exec web python manage.py migrate```

```docker-compose exec web python manage.py createsuperuser```

```docker-compose exec web python manage.py collectstatic --no-input```

Теперь проект доступен по адресу http://localhost/.

Примеры адресов, по которым можно обратиться, чтобы проверить корректную работу проекта:

http://localhost/admin/ - админка,

http://localhost/redoc/ - документация API YaMDB,

http://localhost/api/v1/categories/ - общедоступный эндпоинт API.


### Авторство

Автор инфраструктуры: Татьяна Овчинникова

Авторство разворачиваемого проекта YaMDB принадлежит команде из трёх человек (включая меня). Подробнее можно прочитать в README проекта YaMDB: https://github.com/tanja-ovc/api_yamdb_group_project.
