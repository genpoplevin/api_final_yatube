### Описание:

API для взаимодействия с Yatube посредством обмена JSON сообщениями

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/genpoplevin/api_final_yatube.git
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
Получить список всех публикаций. При указании параметров limit и offset выдача работает с пагинацией.

GET http://127.0.0.1:8000/api/v1/posts/


Создание публикации

POST http://127.0.0.1:8000/api/v1/posts/


Получение и добавление комментариев

GET http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/
POST http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/


Список сообществ

GET http://127.0.0.1:8000/api/v1/groups/

Подписки

GET http://127.0.0.1:8000/api/v1/follow/
POST http://127.0.0.1:8000/api/v1/follow/

Работа с JWT-токенами
```
Получить JWT-токен
POST http://127.0.0.1:8000/api/v1/jwt/create/

Обновить JWT-токен
POST Обновить JWT-токен

Проверить JWT-токен
POST http://127.0.0.1:8000/api/v1/jwt/verify/
