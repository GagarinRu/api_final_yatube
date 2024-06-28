### Описание

Проект «API для Yatube».Бэкенд приложением c APi.

В данном проекте необходимо сделать следующий функционал:

- Создание, обновление и удаление публикаций авторизованными пользователями;
- Создание, обновление и удаление комментариев к публикациями авторизованными пользователями;
- Подписываться и отписываться от авторизованного пользователя;
- Авторизованный пользователь не может подписваться на самого себя;
- Просмотр сообществ
- Фильтрация по полям.

# Установка

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/GagarinRu/api_final_yatube
```

```
cd api_final_yatube
```

Cоздать и активировать виртуальное окружение:

```
python3 -m venv env
```

```
source env/bin/activate
```

Установить зависимости из файла requirements.txt:

```
python3 -m pip install --upgrade pip
```

```
pip install -r requirements.txt
```

Выполнить миграции:

```
python3 manage.py migrate
```

Запустить проект:

```
python3 manage.py runserver
```

### Примеры

- Полуение токена пользователя.

POST-запрос на адрес с указанием имени и пароля пользователя:

```
api/v1/jwt/create/
```
Запрос:

{
    "username": "New_user",
    "password": "Change_me"
}

Ответ:

{
    "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTcxOTYzMjQ5MCwianRpIjoiYTUyMjAwM2JiMDdiNGVmYTk0MzBlZDM5OTMzNDdkNWEiLCJ1c2VyX2lkIjozfQ._VFWX_cVfuYWYZNOEdz4kLFY5tdmmLPZ2psxJBi4R_g",
    "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNzE5NjMyNDkwLCJqdGkiOiJmN2Y2MDAxOGI4MTk0YWQ3YmQxNmNkMjk2YzNjZTkyZCIsInVzZXJfaWQiOjN9.GZYeR02RvOVPRlfVqiTxUhqEvZkx-wF1NyWkns4Ws58"
}

- Создание поста по адресу.

POST-запрос на адресу с обязательным полем "text", в Headers указать token пользователя:

```
http://127.0.0.1:8000/api/v1/posts/
```
Запрос:

{
  "text": "Тестовый пост."
}

Ответ:

{
    "id": 1,
    "author": "New_user",
    "text": "Тестовый пост.",
    "pub_date": "2024-06-28T03:48:44.101711Z",
    "image": null,
    "group": null
}

- Просмотр поста.

Get-запрос по адресу, в Headers указать token пользователя:

```
http://127.0.0.1:8000/api/v1/posts/1/
```

Ответ:

{
    "id": 1,
    "author": "New_user",
    "text": "Тестовый пост.",
    "pub_date": "2024-06-28T03:48:44.101711Z",
    "image": null,
    "group": null
}

- Создание комментария.

POST-запрос на адресу с полями "post" и "text", в Headers указать token пользователя:

```
http://127.0.0.1:8000/api/v1/posts/1/comments/
```

Запрос:

{
        "post": 1,
        "text": "Тестовый комментарий"
}

Ответ:

{
    "id": 1,
    "author": "New_user",
    "text": "Тестовый комментарий",
    "created": "2024-06-28T04:05:47.758939Z",
    "post": 1
}

- Просмотр поста.

Get-запрос по адресу, в Headers указать token пользователя:

```
http://127.0.0.1:8000/api/v1/posts/1/comments/
```

Ответ:

{
    "id": 1,
    "author": "New_user",
    "text": "Тестовый комментарий",
    "created": "2024-06-28T04:05:47.758939Z",
    "post": 1
}

# Автор проекта

https://github.com/GagarinRu/

# Ресурсы

- Документация проекта: http://127.0.0.1:8000/redoc/
- ПО для тестирования API: Postman v11.2.0