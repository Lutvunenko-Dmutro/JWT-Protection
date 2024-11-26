
# Flask JWT Protection API

Це Flask API, яке використовує JWT (JSON Web Token) для захисту доступу до ресурсів. Користувачі можуть отримати токен після успішної аутентифікації, і цей токен буде використовуватися для доступу до захищених ендпоінтів.

## Особливості

- Генерація JWT токенів із терміном дії 30 днів.
- Захист ендпоінтів за допомогою JWT.
- Логін за допомогою користувача "admin" та пароля "adminpassword".
- Використання SQLite для зберігання даних.

## Встановлення

1. Клонуйте репозиторій:
    ```bash
    git clone https://your-repository-url.git
    ```

2. Перейдіть в директорію проекту:
    ```bash
    cd JWT-Protection
    ```

3. Встановіть залежності:
    ```bash
    pip install -r requirements.txt
    ```

4. Створіть та налаштуйте базу даних:
    ```bash
    flask db init
    flask db migrate
    flask db upgrade
    ```

## Запуск

1. Для запуску серверу використовуйте:
    ```bash
    python run.py
    ```

2. Тепер ви можете звертатися до API.

## API

### 1. Логін та отримання токена

**Метод**: `POST`  
**Маршрут**: `/login`

**Тіло запиту**:
```json
{
    "username": "admin",
    "password": "adminpassword"
}
```

**Відповідь**:
```json
{
    "access_token": "your-jwt-token"
}
```

### 2. Отримати список всіх елементів

**Метод**: `GET`  
**Маршрут**: `/item`

**Відповідь**:
```json
[
    {
        "id": 1,
        "name": "Item 1",
        "description": "Description of item 1",
        "price": 19.99
    }
]
```

### 3. Отримати елемент за ID

**Метод**: `GET`  
**Маршрут**: `/item/<item_id>`

**Відповідь**:
```json
{
    "id": 1,
    "name": "Item 1",
    "description": "Description of item 1",
    "price": 19.99
}
```

### 4. Створити новий елемент

**Метод**: `POST`  
**Маршрут**: `/item`

**Тіло запиту**:
```json
{
    "name": "Item 2",
    "description": "Description of item 2",
    "price": 29.99
}
```

**Відповідь**:
```json
{
    "id": 2,
    "name": "Item 2",
    "description": "Description of item 2",
    "price": 29.99
}
```

## Помилки

- **401 Unauthorized**: Якщо токен відсутній або недійсний.
- **403 Forbidden**: Якщо токен прострочений.
- **404 Not Found**: Якщо елемент не знайдено.
#### Зробив Литвиненко Дмитро
