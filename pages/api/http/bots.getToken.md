
# bots.getToken

<%- include('../../../includes/auth/required.md') %>

Создаёт новый ключ доступа для бота. Все предыдущие ключи доступа, выданные этому боту, отзываются.

<aside info>
  Метод вызывается с токеном пользователя, который владеет ботом.
</aside>

## Параметры

<<< PARAMETERS
user_id: uint [REQUIRED]
Идентификатор пользователя бота.
<<<
ip: string?
IPv4 или IPv6, к которому будет привязана сессия.
Note: По умолчанию — текущий IP.
<<<

## Результат

Возвращает объект [`Session`](/objects/Session).

## Коды ошибок

<%- include('../../../includes/errors/head.md') -%>
<%- include('../../../includes/errors/1801.md') -%>

# MARK: Examples

## Request

POST /api/bots.getToken

```bash
curl -X POST "https://monopoly-one.com/api/bots.getToken" \
     -d user_id="1234567890"
     -d access_token="N4WyIZYl9eYRuLOuUYHRmWwj80Zyb4u5yC0N"
```

## Ответ

```json
{
  "code": 0,
  "data": {
    "user_id": 1234567890,
    "access_token": "17t5BQBj5KAHMKCGWM1KW2fBTCnAyGuPxg9M",
    "expires_in": 0,
    "expires": 0
  }
}
```
