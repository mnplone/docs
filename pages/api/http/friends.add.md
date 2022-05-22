
# friends.add

<%- include('../../../includes/auth/required.md') %>

Отправляет запрос дружбы пользователю или принимает входящий запрос дружбы от пользователя.

## Параметры

<<< PARAMETERS
user_id: uint [REQUIRED]
Идентификатор пользователя.
<<<

## Результат

Метод не возвращает данных.

## Коды ошибок

<%- include('../../../includes/errors/head.md') -%>
<%- include('../../../includes/errors/101.md') -%>
<%- include('../../../includes/errors/107.md') -%>

# MARK: Examples

## Request

POST /api/friends.add

```bash
curl -X POST https://monopoly-one.com/api/friends.add
     -d user_id="1"
```

## Ответ

```json
{
  "code": 0
}
```
