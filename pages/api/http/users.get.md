
# users.get

<%- include('../../../includes/auth/optional.md') %>

Возвращает информацию о пользователях по их идентификаторам или доменам.
Если параметры `user_id` и `user_ids` не переданы, то в случае передачи корректного `access_token` будет возвращена информация о текущем пользователе.

## Параметры

<<< PARAMETERS
user_id: uint? | string?
Идентификатор или домен пользователя.
<<<
user_ids: set<uint | string>?
Идентификаторы или домены пользователей.
Note: Максимум — 50 элементов.
<<<
type: string?
Тип информации о пользователе:
`short` — короткая;
другое — полная.
<<<

## Результат

Возвращает `list` объектов [`User`](/objects/User).

# MARK: Examples

## Request

GET /api/users.get

```bash
curl https://monopoly-one.com/api/users.get?user_ids=193,doge
```

## Ответ

```json
{
  "code": 0,
  "data": [
    {
      "user_id": 193,
      "domain": "meowbot",
      "approved": 1,
      "nick": "meowbot",
      "nicks_old": [],
      "gender": 1,
      "avatar": "https://pp.userapi.com/c834302/v834302095/15789e/hXua9eDqZO4.jpg",
      "online": 1,
      "rank": {
        "hidden": 1
      },
      "games": 2,
      "games_wins": 0,
      "xp": 1503,
      "xp_level": 6
    },
    {
      "user_id": 514985,
      "domain": "doge",
      "nick": "Собака коммунизма",
      "nicks_old": [
        "Валорантер Собака",
        "Собака коммунизма",
        "HukuTka",
        "Собака коммунизма",
        "Винни-Пух",
        "Собака коммунизма",
        "Mono",
        "Hriundel"
      ],
      "gender": 0,
      "avatar": "https://cdn.discordapp.com/attachments/473133635042541581/550653772775424010/749fa4af.jpg",
      "rank": {
        "hidden": 1
      },
      "games": 2338,
      "games_wins": 1108,
      "xp": 237491,
      "xp_level": 129
    }
  ]
}
```
