# Yatube API

REST API для социальной сети Yatube. Позволяет создавать посты, комментировать их, подписываться на авторов и объединять публикации по группам.

## Описание

Yatube API предоставляет доступ к функциям социальной сети через HTTP-запросы. Поддерживает аутентификацию по JWT-токенам. Неаутентифицированные пользователи могут читать данные (посты, комментарии, группы), но для создания контента и подписок требуется авторизация.

## Технологии

- Python 3.9+
- Django 3.2
- Django REST Framework 3.12
- SimpleJWT
- Djoser

## Установка

1. Клонируйте репозиторий:
   ```bash
   git clone <url-репозитория>
   cd api-final-yatube-ad
   ```

2. Создайте и активируйте виртуальное окружение:
   ```bash
   python -m venv venv
   source venv/bin/activate  # Linux/macOS
   venv\Scripts\activate     # Windows
   ```

3. Установите зависимости:
   ```bash
   pip install -r requirements.txt
   ```

4. Выполните миграции:
   ```bash
   cd yatube_api
   python manage.py migrate
   ```

5. Запустите сервер:
   ```bash
   python manage.py runserver
   ```

Документация API доступна по адресу: http://127.0.0.1:8000/redoc/

## Примеры запросов

### Получение JWT-токена
```http
POST /api/v1/jwt/create/
Content-Type: application/json

{
  "username": "user",
  "password": "password"
}
```

### Получение списка постов
```http
GET /api/v1/posts/
```

### Создание поста (требуется авторизация)
```http
POST /api/v1/posts/
Authorization: Bearer <ваш_токен>
Content-Type: application/json

{
  "text": "Текст поста"
}
```

### Получение комментариев к посту
```http
GET /api/v1/posts/{post_id}/comments/
```

### Подписка на пользователя (требуется авторизация)
```http
POST /api/v1/follow/
Authorization: Bearer <ваш_токен>
Content-Type: application/json

{
  "following": "username"
}
```

### Получение своих подписок с поиском
```http
GET /api/v1/follow/?search=username
Authorization: Bearer <ваш_токен>
```
