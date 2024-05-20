# SpringProject
Вимоги до функціоналу

    Реєстрація користувачів: Користувачі можуть створювати облікові записи.
    Авторизація користувачів: Користувачі можуть входити до своїх облікових записів.
    Пошук книг: Користувачі можуть шукати книги за назвою, автором, ISBN та іншими параметрами.
    Перегляд деталей книги: Користувачі можуть переглядати деталі книги, включаючи опис, автора, дату видання та інші метадані.
    Створення/Редагування/Видалення записів книг: Адміністратори можуть додавати, редагувати та видаляти записи книг.
    Резервування книг: Користувачі можуть резервувати книги онлайн.
    Перегляд стану резервування: Користувачі можуть переглядати статус своїх резервувань.
    Перегляд історії користувача: Користувачі можуть переглядати історію своїх запозичень та резервувань.
    Оцінка та відгуки на книги: Користувачі можуть залишати оцінки та відгуки на книги.
    Нотифікації: Система надсилає сповіщення користувачам про статус резервування та повернення книг.

Поведінка системи та REST API ендпоінти

    Реєстрація користувача
        Метод: POST
        Ендпоінт: /api/users/register
        Тіло запиту: { "username": "string", "password": "string", "email": "string" }
        Відповідь: { "message": "User registered successfully", "userId": "number" }

    Авторизація користувача
        Метод: POST
        Ендпоінт: /api/users/login
        Тіло запиту: { "username": "string", "password": "string" }
        Відповідь: { "token": "string", "userId": "number" }

    Пошук книг
        Метод: GET
        Ендпоінт: /api/books/search
        Параметри запиту: ?query=string
        Відповідь: { "books": [ { "id": "number", "title": "string", "author": "string", "isbn": "string" } ] }

    Перегляд деталей книги
        Метод: GET
        Ендпоінт: /api/books/{id}
        Відповідь: { "id": "number", "title": "string", "author": "string", "description": "string", "isbn": "string", "publishedDate": "date" }

    Створення запису книги
        Метод: POST
        Ендпоінт: /api/books
        Тіло запиту: { "title": "string", "author": "string", "description": "string", "isbn": "string", "publishedDate": "date" }
        Відповідь: { "message": "Book created successfully", "bookId": "number" }

    Редагування запису книги
        Метод: PUT
        Ендпоінт: /api/books/{id}
        Тіло запиту: { "title": "string", "author": "string", "description": "string", "isbn": "string", "publishedDate": "date" }
        Відповідь: { "message": "Book updated successfully" }

    Видалення запису книги
        Метод: DELETE
        Ендпоінт: /api/books/{id}
        Відповідь: { "message": "Book deleted successfully" }

    Резервування книги
        Метод: POST
        Ендпоінт: /api/reservations
        Тіло запиту: { "userId": "number", "bookId": "number", "reservationDate": "date" }
        Відповідь: { "message": "Book reserved successfully", "reservationId": "number" }

    Перегляд стану резервування
        Метод: GET
        Ендпоінт: /api/reservations/{userId}
        Відповідь: { "reservations": [ { "reservationId": "number", "bookId": "number", "status": "string" } ] }

    Оцінка та відгуки на книги
        Метод: POST
        Ендпоінт: /api/reviews
        Тіло запиту: { "userId": "number", "bookId": "number", "rating": "number", "review": "string" }
        Відповідь: { "message": "Review submitted successfully" }
