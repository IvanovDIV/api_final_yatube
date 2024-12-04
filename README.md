# api_final
# Описание
Yatube — это платформа для обмена мыслями, идеями и фотографиями. Данное API предоставляет разработчикам возможность интегрировать функции Yatube в свои приложения. API использует архитектуру RESTful и JSON для обмена данными.

Установка

Клонируйте репозиторий:

клонируйте репозиторий 
`git https://github.com/IvanovDIV/api_final_yatube.git`
cd yatube_api

Создайте и активируйте виртуальное окружение:

`python3 -m venv env`
`source env/bin/activate # Linux/macOS`
`env\Scripts\activate # Windows`

Установите зависимости:

`python3 -m pip установить --обновить pip`
`pip установить -r requirements.txt`

Выполните миграции:

python manage.py миграция
Запустите сервер разработки:

python manage.py сервер запуска
Примеры запросов
Аутентификация (JWT):

Получение токена:

curl -X POST -d "имя_пользователя=<имя_пользователя>&пароль=<пароль>" /api/v1/jwt/create/
Обновление токена:

curl -X POST -d "refresh=<токен_обновления>" /api/v1/jwt/refresh/
Работа с публикациями (требуется авторизация):

Получение всех публикаций (с пагинацией):

curl -H "Авторизация: на предъявителя <access_token>" /api/v1/posts/?limit=10&offset=0
Создание публикации:

curl -X POST -H "Authorization: Bearer <access_token>" -d '{"text": "Мой новый пост", "group": 1}' /api/v1/posts/
Получение публикации по ID:

curl -H "Авторизация: предъявитель <токен доступа>" /api/v1/posts/<post_id>/
Изменение публикации (только автор):

curl -X PUT -H "Авторизация: предъявитель <токен доступа>" -d '{"текст": "измененный текст"}' /api/v1/posts/<post_id>/
Удаление публикации (только автор):

curl -X DELETE -H "Авторизация: на предъявителя <access_token>" /api/v1/posts/<post_id>/
Работа с комментариями (требуется авторизация):

Получение комментариев к посту:

curl -H "Авторизация: на предъявителя <access_token>" /api/v1/сообщения/<post_id>/комментарии/
Создание комментария:

curl -X POST -H "Авторизация: предъявитель <токен доступа>" -d '{"текст": "Мой комментарий"}' /api/v1/posts/<post_id>/comments/
Работа с группами (не требует авторизации):

Получение списка групп:

curl / api / v1 /группы/
Получение группы по ID:

curl /api/v1/groups/<идентификатор_группы>/
Работа с подписками (требуется авторизация):

Получение всех подписок:

curl -H "Авторизация: на предъявителя <access_token>" /api/v1/следовать/
Подписка на пользователя:

curl -X POST -H "Авторизация: на предъявителя <access_token>" -d '{"following": "<имя пользователя>"}' /api/v1/следовать/
Документация API
Полная документация API доступна по адресу: http://127.0.0.1:8000/redoc/
