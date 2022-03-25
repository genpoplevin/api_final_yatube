### Описание:

API для взаимодействия с Yatube* посредством обмена JSON сообщениями

*yatube.com - социальная сеть, где можно публиковать свои посты, подписываться на понравившихся авторов

### Как запустить проект:

Клонировать репозиторий:

```
git clone https://github.com/genpoplevin/api_final_yatube.git
```

Перейти в репозиторий в командной строке:
```
cd api_final_yatube
```

Cоздать виртуальное окружение:

```
python3 -m venv env
либо
python -m venv venv
```

Активировать виртуальное окружение:
```
source env/bin/activate
либо
source venv/Scripts/activate
```

Обновить менеджер пакетов pip:
```
python3 -m pip install --upgrade pip
```

Установить зависимости из файла requirements.txt:

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

Получение публикаций.
```
Получить список всех публикаций. При указании параметров limit и offset выдача работает с пагинацией.

GET yatube.com/api/v1/posts/

Пример ответа:
{
  "count": 123,
  "next": "http://api.example.org/accounts/?offset=400&limit=100",
  "previous": "http://api.example.org/accounts/?offset=200&limit=100",
  "results": [
    {
      "id": 0,
      "author": "string",
      "text": "string",
      "pub_date": "2021-10-14T20:41:29.648Z",
      "image": "string",
      "group": 0
    }
  ]
}

Создание публикации

POST yatube.com/api/v1/posts/

Пример запроса:
{
  "text": "string",
  "image": "string",
  "group": 0
}

Пример ответа:
{
  "id": 0,
  "author": "string",
  "text": "string",
  "pub_date": "2019-08-24T14:15:22Z",
  "image": "string",
  "group": 0
}

Получение публикации по id

GET yatube.com/api/v1/posts/{id}/

Пример ответа:
{
  "id": 0,
  "author": "string",
  "text": "string",
  "pub_date": "2019-08-24T14:15:22Z",
  "image": "string",
  "group": 0
}

Обновление публикации

PUT yatube.com/api/v1/posts/{id}/

Пример запроса:
{
  "text": "string",
  "image": "string",
  "group": 0
}

Пример ответа:
{
  "id": 0,
  "author": "string",
  "text": "string",
  "pub_date": "2019-08-24T14:15:22Z",
  "image": "string",
  "group": 0
}

Частичное обновление публикации

PATCH yatube.com/api/v1/posts/{id}/

Пример запроса:
{
  "text": "string",
  "image": "string",
  "group": 0
}

Пример ответа:
{
  "id": 0,
  "author": "string",
  "text": "string",
  "pub_date": "2019-08-24T14:15:22Z",
  "image": "string",
  "group": 0
}

Удаление публикации

DELETE yatube.com/api/v1/posts/{id}/

Пример ответа:
{
  "detail": "Учетные данные не были предоставлены."
}
```

Получение и добавление комментариев
```
Получение всех комментариев к публикации

GET yatube.com/api/v1/posts/{post_id}/comments/

Пример ответа:
[
  {
    "id": 0,
    "author": "string",
    "text": "string",
    "created": "2019-08-24T14:15:22Z",
    "post": 0
  }
]

Добавление комментария

POST yatube.com/api/v1/posts/{post_id}/comments/

Пример запроса:
{
  "text": "string"
}

Пример ответа:
{
  "id": 0,
  "author": "string",
  "text": "string",
  "created": "2019-08-24T14:15:22Z",
  "post": 0
}

Получение комментария к публикации по id

GET yatube.com/api/v1/posts/{post_id}/comments/{id}/

Пример ответа:

{
  "id": 0,
  "author": "string",
  "text": "string",
  "created": "2019-08-24T14:15:22Z",
  "post": 0
}

Обновление комментария

PUT http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/{id}/

Пример запроса:
{
  "text": "string"
}

Пример ответа:
{
  "id": 0,
  "author": "string",
  "text": "string",
  "created": "2019-08-24T14:15:22Z",
  "post": 0
}

Частичное обновление комментария

PATCH http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/{id}/

Пример запроса:
{
  "text": "string"
}

Пример ответа:
{
  "id": 0,
  "author": "string",
  "text": "string",
  "created": "2019-08-24T14:15:22Z",
  "post": 0
}

Удаление комментария

DELETE http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/{id}/

Пример ответа:
{
  "detail": "Учетные данные не были предоставлены."
}
```

Список сообществ
```
GET http://127.0.0.1:8000/api/v1/groups/

Пример ответа:
[
  {
    "id": 0,
    "title": "string",
    "slug": "string",
    "description": "string"
  }
]

Информация о сообществе

GET http://127.0.0.1:8000/api/v1/groups/{id}/

Пример ответа:
{
  "id": 0,
  "title": "string",
  "slug": "string",
  "description": "string"
}
```

Подписки
```
Возвращает все подписки пользователя, сделавшего запрос. Анонимные запросы запрещены.

GET http://127.0.0.1:8000/api/v1/follow/

Пример ответа:
[
  {
    "user": "string",
    "following": "string"
  }
]

Подписка пользователя от имени которого сделан запрос на пользователя переданного в теле запроса. Анонимные запросы запрещены.

POST http://127.0.0.1:8000/api/v1/follow/

Пример запроса:
{
  "following": "string"
}

Пример ответа:
{
  "user": "string",
  "following": "string"
}
```

Работа с JWT-токенами
```
Получить JWT-токен

POST http://127.0.0.1:8000/api/v1/jwt/create/

Пример запроса:
{
  "username": "string",
  "password": "string"
}

Пример ответа:
{
  "refresh": "string",
  "access": "string"
}

Обновить JWT-токен

POST http://127.0.0.1:8000/api/v1/jwt/refresh/

Пример запроса:
{
  "refresh": "string"
}

Пример ответа:
{
  "access": "string"
}

Проверить JWT-токен

POST http://127.0.0.1:8000/api/v1/jwt/verify/

Пример запроса:
{
  "token": "string"
}

Пример ответа:
{
  "token": [
    "Обязательное поле."
  ]
}
