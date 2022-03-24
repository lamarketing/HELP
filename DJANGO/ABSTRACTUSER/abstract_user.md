### Расширение модели User через AbstractUser
Лучше делать такую модель в начале каждого проекта, 
потому что вносить изменения необязательно в начале,
а потом применить такой способ уже не получится.

СТРОГО ПРИ СОЗДАНИИ ПРОЕКТА - ДО MIGRATE!!!

1. Создать приложение _abstactuser_ в папке проекта
```
$ mkdir abstactuser
$ cd abstactuser
$ touch models.py
```
2. Внести изменения в _abstactuser/models.py_
```
"""abstactuser/models.py"""

import uuid

from django.db import models
from django.contrib.auth.models import AbstractUser


class User(AbstractUser):
    id = models.UUIDField(primary_key=True, default=uuid.uuid4)
    ...
```
3. Добавить в настройках приложение и AUTH_USER_MODEL
```
"""setting.py"""

INSTALLED_APPS = [
    ...
    'django.contrib.staticfiles',
    'abstractuser',
    ...
]

AUTH_USER_MODEL = 'abstractuser.User'
```
4. Сделать первую миграцию
```
$ python manage.py makemigrations abstractuser
$ python manage.py migrate
```
5. Все остальное
```
$ python manage.py makemigrations <app1> <app2> ...
$ python manage.py migrate
```