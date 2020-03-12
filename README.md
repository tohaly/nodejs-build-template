# Сервер для проекта "Проект"

Version: v.0.0.1

## Описание Проекта

Данный сервер разработан на node.js с применением  express.js.

## Как найти

Сервер можной найти по следующим адресам:

#### Бэкэнд

https://api.mesto-spa.ml/

https://www.api.mesto-spa.ml/

#### Фронтенд

https://mesto-spa.ml/

https://www.mesto-spa.ml/

## Используемые технологии:

JS, GIT, Eslint, Node.js, express.js.

## Локальный запуск

1. Склонировать репозиторий
2. Доставить отсутствующие модули npm
   ```
       npm install
   ```
3. Запустить локальный сервер
   ```
       npm run dev
   ```

## Внесение изменений

При необходимости, после внесения изменений, запустить тестирование

```
    npm run eslint
```

## API

### `/signup`

- Описание: Создания пользователя на сервере.
- Метод: `POST`;
- Headers:

```
Content-Type: application/json
```

- Параметры:

```
name: имя пользователя, string;
about - информация о пользователе, string;
avatar - ссылка на аватар пользователя, string;
email - почта для регистрации, string;
password - пароль, string.
```

- Пример тела запроса:

```
{
  "name": "Рагнар Лодброк",
  "about": "Король",
  "avatar": "avatar.com/ragnar.jpg",
  "email": "ragnar@gmail.com"
  "password": "p2As&dww0rd"
}
```

- Пример ответа:

```
 {
  "_id": "5e5105023443980914d76c09",
  "name": "Рагнар Лодброк",
  "about": "Король",
  "avatar": "avatar.com/ragnar.jpg",
  "email": "ragnar@gmail.com"
  }
```

### `/signin`

- Описание: Авторизация пользователя на сервере.
- Метод: `POST`;
- Headers:

```
Content-Type: application/json
```

- Параметры:

```
email - почта для регистрации, string;
password - пароль, string.
```

- Пример тела запроса:

```
{
  "email": "ragnar@gmail.com"
  "password": "p2As&dww0rd"
}
```

- Пример ответа:

```
{
Authorization: Bearer eyJhbG...Td3LIqXAw  //Пример токена авторизации
}
```

### `/users`

- Описание: Получение списка пользователей.
- Метод: `GET`;
- Headers:

```
Authorization: Bearer eyJhbG...Td3LIqXAw  //Пример токена авторизации
```

- Пример ответа:

```
{
  "data": [
    {
        "_id": "5e43f910b70cfe185c99defd",
        "name": "Ивар Логдброк",
        "about": "Сын",
        "avatar": "avatar.com/ivar.jpg",
        "email": "ivar@gmail.com"
    },

    .......................

    .......................

    {
      "_id": "5e5105023443980914d76c09",
      "name": "Рагнар Лодброк",
      "about": "Король",
      "avatar": "avatar.com/ragnar.jpg",
      "email": "ragnar@gmail.com"
    }
  ]
}
```

### `/users/:iserId`

- Описание: Получить пользователя по id. Здесь `userId` - уникальный `_id` присвоенный каждому пользователю.
- Метод: `GET`;
- Headers:

```
Authorization: Bearer eyJhbG...Td3LIqXAw  //Пример токена авторизации
```

- Пример ответа:

```
    {
      "_id": "5e43f910b70cfe185c99defd",
      "name": "Ивар Логдброк",
      "about": "Сын",
      "avatar": "avatar.com/ivar.jpg",
      "email": "ivar@gmail.com"
    }
```

### `/users/me`

- Описание: Обновление данных пользователя, а именно имя и инормацию о пользователе.
- Метод: `PATCH`;
- Headers:

```
Content-Type: application/json

Authorization: Bearer eyJhbG...Td3LIqXAw  //Пример токена авторизации
```

- Параметры:

```
  name - имя пользователя, string;
  about - информация о пользователе, string;
```

- Пример тела запроса:

```
{
  "name": "Бьёрн";
  "about": Старшый сын;
}
```

- Пример ответа:

```
  {
    "_id": "5e43f910b70cfe185c99defd",
    "name": "Бьёрн",
    "about": "Старшый сын",
    "avatar": "avatar.com/ivar.jpg",
    "email": "ivar@gmail.com"
  }
```

### `/users/me/avatar`

- Описание: Обновление аватар пользователя.
- Метод: `PATCH`;
- Headers:

```
Content-Type: application/json

Authorization: Bearer eyJhbG...Td3LIqXAw  //Пример токена авторизации
```

- Параметры:

```
avatar - ссылка на автар пользователя, string;
```

- Пример тела запроса:

```
{
    "avatar": "avatar.com/byorn.jpg",
}
```

- Пример ответа:

```
  {
    "_id": "5e43f910b70cfe185c99defd",
    "name": "Бьёрн",
    "about": "Старшый сын",
    "avatar": "avatar.com/byorn.jpg",
    "email": "ivar@gmail.com"
  }
```

### `/cards`

- Описание: Получение списка карточек.
- Метод: `GET`;
- Headers:

```
Authorization: Bearer eyJhbG...Td3LIqXAw  //Пример токена авторизации
```

- Пример ответа:

```
{
    "data": [
        {
            "likes": [],
            "_id": "5e45434d76daf744c05214f5",
            "name": "Test card 1",
            "link": "cardr.com/card1.jpg",
            "owner": "5e4420b893964a116479cacc",
            "createdAt": "2020-02-13T12:38:37.478Z"
        },

        ..................

        ..................

        {
            "likes": [],
            "_id": "5e4d395b2982ee11d8425733",
            "name": "Test card 99",
            "link": "cardr.com/card99.jpg",
            "owner": "5e4d37f34a5e6d35647cb6d3",
            "createdAt": "2020-02-19T13:34:19.222Z"
        }
    ]
}
```

### `/cards`

- Описание: Создания пользователя на сервере.
- Метод: `POST`;
- Headers:

```
Content-Type: application/json

Authorization: Bearer eyJhbG...Td3LIqXAw  //Пример токена авторизации
```

- Параметры:

```
name - имя карточки, string;
link - ссылка на карточку, string.
```

- Пример тела запроса:

```
{
  "name": "Card 100",
  "link": "cards.com/card100"
}
```

- Пример ответа:

```
    {
      "likes": [], // Массив с лайкнувшими пользователями
      "_id": "5e513f3e40276d2fac54e47a",
      "name": "Card 100",
      "link": "cards.com/card100",
      "owner": "5e4d37f34a5e6d35647cb6d3",  // Владелец карточки
      "createdAt": "2020-02-22T14:48:30.203Z" // Дата создания
    }

```

### `/cards/:cardId`

- Описание: Удаляет карточку из базы данных.
- Метод: `DELETE`;
- Headers:

```
Authorization: Bearer eyJhbG...Td3LIqXAw  //Пример токена авторизации
```

- Пример ответа:

```
  {
    "message": "Пост успешно удален!"
  }
```

### `/cards/:cardId/likes`

- Описание: Лайк карточки.
- Метод: `PUT`;
- Headers:

```
Authorization: Bearer eyJhbG...Td3LIqXAw  //Пример токена авторизации
```

- Пример ответа:

```
    {
      "likes": [
          "5e4d37f34a5e6d3564dvs8vd"
          "5e4d37f347feg735647cfgd9"
          "5e4d37f34a5e6d35647cb6d3"  // _id авторизированного пользователя, который лайкунл карточку
      ],
      "_id": "5e5142be16bf5323d0c875c7",
      "name": "Card 100",
      "link": "cards.com/card100",
      "owner": "5e4d37f34a5e6d35647cb6d3",
      "createdAt": "2020-02-22T15:03:26.180Z"
    }

```

### `/cards/:cardId/likes`

- Описание: Удаление лайка с карточки.
- Метод: `DELETE`;
- Headers:

```
Authorization: Bearer eyJhbG...Td3LIqXAw  //Пример токена авторизации
```

- Пример ответа:

```
    {
      "likes": [
          "5e4d37f34a5e6d3564dvs8vd"
          "5e4d37f347feg735647cfgd9"
          // Из массива удален _id пользователя
      ],
      "_id": "5e5142be16bf5323d0c875c7",
      "name": "Card 100",
      "link": "cards.com/card100",
      "owner": "5e4d37f34a5e6d35647cb6d3",
      "createdAt": "2020-02-22T15:03:26.180Z"
    }

```
