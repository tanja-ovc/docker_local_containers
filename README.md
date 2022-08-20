# Docker YaMDB Local

### Проект YaMDB с инфраструктурой для локального деплоя
(версия без инфраструктуры: https://github.com/tanja-ovc/api_yamdb_group_project)

- Данный проект посвящен созданию инфраструктуры для __локального__ деплоя уже существующего проекта YaMDB (https://github.com/tanja-ovc/api_yamdb_group_project).

### Установка
Клонировать репозиторий и перейти в него в командной строке:

```git@github.com:tanja-ovc/docker_local_containers.git```

Убедиться, что находитесь в директории ```docker_local_containers/```.

Cоздать и активировать виртуальное окружение:

```python3 -m venv venv```

```source env/bin/activate```

При необходимости обновить pip:

```python3 -m pip install --upgrade pip```

Установить зависимости из файла requirements.txt:

```cd api_yamdb```

```pip install -r requirements.txt```

Выполнить миграции:

```python3 manage.py migrate```

### Запуск проекта

Для запуска контейнера необходимо обращение к DockerHub и установленный Docker.

Выполните команду ```docker pull tanjadocker/infra_yamdb:v1.17.12.21```, где ```v1.17.12.21``` - номер версии проекта. Допускается обращение и без тега: ```docker pull tanjadocker/infra_yamdb:latest``` (для загрузки последней версии).

Соберите контейнеры:

```docker-compose up```

Выполните по очереди команды (выполнить миграции, создать суперпользователя и собрать статику):

```docker-compose exec web python manage.py migrate```
```docker-compose exec web python manage.py createsuperuser```
```docker-compose exec web python manage.py collectstatic --no-input```

Теперь проект доступен по адресу http://localhost/.


### Авторы проекта YamDB (ноябрь 2021)

_Алексей Борисов_ - автор системы регистрации и аутентификации, права доступа, работа с токеном, система подтверждения через e-mail.

_Татьяна Овчинникова_ - автор системы работы с категориями, жанрами и произведениями: модели, представления и эндпойнты для них.

_Василий Кузьминых_ - автор системы отзывов и комментариев: модели, представления, эндпойнты, рейтинги произведений. Инициатор разработки и автор manage-команды для внесения данных из файлов формата .csv в существующую базу данных.


### Автор инфраструктуры (январь 2022)
_Татьяна Овчинникова_

