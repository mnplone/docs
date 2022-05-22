
# friends.delete

<%- include('../../../includes/auth/required.md') %>

Удаляет пользователю из друзей или отклоняет входящий запрос дружбы от пользователя.

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

# MARK: Examples

## Request

POST /api/friends.delete

```bash
curl -X POST https://monopoly-one.com/api/friends.delete
     -d user_id="1"
```

## Ответ

```json
{
  "code": 0
}
```
