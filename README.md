# Docker YamDB
## Блок Docker. Локальная контейнеризация (спринт 12)

### Описание
Инфраструктура для контейнеризации проекта YamDB.

### Установка
Клонировать репозиторий и перейти в него в командной строке:

```git@github.com:tanja-ovc/infra_sp2.git```

Убедиться, что находитесь в директории ```infra_sp2/```.

Cоздать и активировать виртуальное окружение:

```python -m venv venv```

```source env/bin/activate```

При необходимости обновить pip:

```python -m pip install --upgrade pip```

Установить зависимости из файла requirements.txt:

```cd api_yamdb```

```pip install -r requirements.txt```

Выполнить миграции:

```python manage.py migrate```

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

### Авторы
_Татьяна Овчинникова_
