
# gchat.send

<%- include('../../../includes/auth/required.md') %>

Отправляет сообщение в общий чат.

## Параметры

<<< PARAMETERS
message: string [REQUIRED]
Текст сообщения. Если сообщение начинается с `!`, то оно не будет отображаться в интерфейсах чата, но будет видно через API — это удобно для отправки команд ботам.
<<<
is_public: bit?
Будет ли сообщение публичным, даже если в сообщении не упомянуты пользователи.
Данный параметр доступен только [ботам](/bots).
<<<

## Результат

Возвращает идентификатор сообщения `msg_id`.

## Коды ошибок

<%- include('../../../includes/errors/head.md') -%>
<%- include('../../../includes/errors/104.md') -%>
<%- include('../../../includes/errors/1203.md') -%>

# MARK: Examples

## Request

POST /api/gchat.send

```bash
curl -X POST "https://monopoly-one.com/api/gchat.send" \
     -d message="hello world" \
     -d access_token="M39zODkBtdrZqBPhnMAkh04fKHD8q7i91hFL"
```

## Ответ

```json
{
  "code": 0,
  "data": {
    "msg_id": "DGN5pQbGNcM"
  }
}
```
