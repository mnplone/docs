
# friends.getRequests

<%- include('../../../includes/auth/required.md') %>

Возвращает информацию о пользователях, запросивших дружбу с текущим пользователем.

## Параметры

<<< PARAMETERS
type: string?
Тип информации о друзьях пользователя:
`short` — короткая;
другое — полная.
<<<
<%- include('../../../includes/parameters/offset.md') -%>
<%- include('../../../includes/parameters/count.md') -%>

## Результат

Возвращает `dictionary<string, any>` со следующими параметрами:

<<< PARAMETERS
count: uint
Общее количество запросов в друзья.
<<<
requests: list<[User](/objects/User)>
Данные о пользователях, запросивших дружбу с текущим пользователем.
<<<

# MARK: Examples

## Request

GET /api/friends.getRequests

```bash
curl https://monopoly-one.com/api/friends.getRequests?count=3&access_token=IAETZrCxkN92Jj5GitsaI19U1ESciJv3FedP
```

## Ответ

```json
{
  "code": 0,
  "data": {
    "count": 273,
    "requests": [
      {
        "user_id": 779568,
        "nick": "Twelfth",
        "nicks_old": [
          "Danil_Nk",
          "Danil_Gamer"
        ],
        "gender": 0,
        "avatar": "https://d1.dogecdn.wtf/811281362967461888/psQGXNlRDvZV.jpg",
        "rank": {
          "hidden": 1
        },
        "games": 338,
        "games_wins": 100,
        "xp": 14854,
        "xp_level": 27,
        "friendship": 3
      },
      {
        "user_id": 885203,
        "nick": "Anuar",
        "nicks_old": [
          "A8",
          "◖Блудный сын◗",
          "◖Блудный сын ◗",
          "RHUL",
          "ZabiksKZ",
          "Anuar"
        ],
        "gender": 0,
        "avatar": "https://cdn.discordapp.com/attachments/473133635042541581/695445207579230208/9661af02.png",
        "rank": {
          "hidden": 1
        },
        "games": 436,
        "games_wins": 242,
        "xp": 31004,
        "xp_level": 42,
        "friendship": 3
      },
      {
        "user_id": 544462,
        "nick": "Егор",
        "nicks_old": [],
        "gender": 0,
        "avatar": "https://sun9-3.userapi.com/c840721/v840721596/62456/W-Nl5VVd6YQ.jpg",
        "rank": {
          "hidden": 1
        },
        "games": 44,
        "games_wins": 9,
        "xp": 1321,
        "xp_level": 5,
        "friendship": 3
      }
    ]
  }
}
```
