## Вимоги до функціоналу

1. **Реєстрація користувачів**: Користувачі можуть створювати облікові записи.
2. **Авторизація користувачів**: Користувачі можуть входити до своїх облікових записів.
3. **Пошук книг**: Користувачі можуть шукати книги за назвою, автором, ISBN та іншими параметрами.
4. **Перегляд деталей книги**: Користувачі можуть переглядати деталі книги, включаючи опис, автора, дату видання та інші метадані.
5. **Створення/Редагування/Видалення записів книг**: Адміністратори можуть додавати, редагувати та видаляти записи книг.
6. **Резервування книг**: Користувачі можуть резервувати книги онлайн.
7. **Перегляд стану резервування**: Користувачі можуть переглядати статус своїх резервувань.
8. **Перегляд історії користувача**: Користувачі можуть переглядати історію своїх запозичень та резервувань.
9. **Оцінка та відгуки на книги**: Користувачі можуть залишати оцінки та відгуки на книги.
10. **Нотифікації**: Система надсилає сповіщення користувачам про статус резервування та повернення книг.

## Поведінка системи та REST API ендпоінти

### Реєстрація користувача
- **Метод**: POST
- **Ендпоінт**: `/api/users/register`
- **Тіло запиту**:
    ```json
    {
      "username": "string",
      "password": "string",
      "email": "string"
    }
    ```
- **Відповідь**:
    ```json
    {
      "message": "User registered successfully",
      "userId": "number"
    }
    ```

### Авторизація користувача
- **Метод**: POST
- **Ендпоінт**: `/api/users/login`
- **Тіло запиту**:
    ```json
    {
      "username": "string",
      "password": "string"
    }
    ```
- **Відповідь**:
    ```json
    {
      "token": "string",
      "userId": "number"
    }
    ```

### Пошук книг
- **Метод**: GET
- **Ендпоінт**: `/api/books/search`
- **Параметри запиту**: `?query=string`
- **Відповідь**:
    ```json
    {
      "books": [
        {
          "id": "number",
          "title": "string",
          "author": "string",
          "isbn": "string"
        }
      ]
    }
    ```

### Перегляд деталей книги
- **Метод**: GET
- **Ендпоінт**: `/api/books/{id}`
- **Відповідь**:
    ```json
    {
      "id": "number",
      "title": "string",
      "author": "string",
      "description": "string",
      "isbn": "string",
      "publishedDate": "date"
    }
    ```

### Створення запису книги
- **Метод**: POST
- **Ендпоінт**: `/api/books`
- **Тіло запиту**:
    ```json
    {
      "title": "string",
      "author": "string",
      "description": "string",
      "isbn": "string",
      "publishedDate": "date"
    }
    ```
- **Відповідь**:
    ```json
    {
      "message": "Book created successfully",
      "bookId": "number"
    }
    ```

### Редагування запису книги
- **Метод**: PUT
- **Ендпоінт**: `/api/books/{id}`
- **Тіло запиту**:
    ```json
    {
      "title": "string",
      "author": "string",
      "description": "string",
      "isbn": "string",
      "publishedDate": "date"
    }
    ```
- **Відповідь**:
    ```json
    {
      "message": "Book updated successfully"
    }
    ```

### Видалення запису книги
- **Метод**: DELETE
- **Ендпоінт**: `/api/books/{id}`
- **Відповідь**:
    ```json
    {
      "message": "Book deleted successfully"
    }
    ```

### Резервування книги
- **Метод**: POST
- **Ендпоінт**: `/api/reservations`
- **Тіло запиту**:
    ```json
    {
      "userId": "number",
      "bookId": "number",
      "reservationDate": "date"
    }
    ```
- **Відповідь**:
    ```json
    {
      "message": "Book reserved successfully",
      "reservationId": "number"
    }
    ```

### Перегляд стану резервування
- **Метод**: GET
- **Ендпоінт**: `/api/reservations/{userId}`
- **Відповідь**:
    ```json
    {
      "reservations": [
        {
          "reservationId": "number",
          "bookId": "number",
          "status": "string"
        }
      ]
    }
    ```

### Оцінка та відгуки на книги
- **Метод**: POST
- **Ендпоінт**: `/api/reviews`
- **Тіло запиту**:
    ```json
    {
      "userId": "number",
      "bookId": "number",
      "rating": "number",
      "review": "string"
    }
    ```
- **Відповідь**:
    ```json
    {
      "message": "Review submitted successfully"
    }
    ```
