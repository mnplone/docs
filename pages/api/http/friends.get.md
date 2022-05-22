
# friends.get

<%- include('../../../includes/auth/optional.md') %>

Возвращает информацию о друзьях пользователя.

## Параметры

<<< PARAMETERS
user_id: uint? | string?
Идентификатор или домен пользователя, друзья которого запрашиваются.
Note: По умолчанию равен идентификатору текущего пользователя.
<<<
online: bit? = 0
Возвращать ли только друзей, которые сейчас онлайн.
<<<
add_user: bit? = 0
Вернуть ли данные о самом пользователе.
<<<
type: string?
Тип информации о друзьях пользователя:
`short` — короткая;
другое — полная.
<<<
<%- include('../../../includes/parameters/offset.md') -%>
<%- include('../../../includes/parameters/count.md') -%>

## Результат

Возвращает `dictionary<string, any?>` со следующими параметрами:

<<< PARAMETERS
count: uint
Общее количество друзей пользователя. Если был передан параметр `online=1`, то этот параметр показывает количество друзей онлайн.
<<<
friends: list<[User](/objects/User)>
Данные о друзьях пользователя.
<<<
user: [User](/objects/User)?
Данные о пользователе, друзья которого были запрошены.
<<<

## Коды ошибок

<%- include('../../../includes/errors/head.md') -%>
<%- include('../../../includes/errors/101.md') -%>

# MARK: Examples

## Request

GET /api/friends.get

```bash
curl https://monopoly-one.com/api/friends.get?user_id=2&count=3
```

## Ответ

```json
{
  "code": 0,
  "data": {
    "count": 108,
    "friends": [
      {
        "user_id": 1,
        "domain": "kirick",
        "approved": 1,
        "nick": "kirick",
        "nicks_old": [],
        "gender": 0,
        "avatar": "https://i.dogecdn.wtf/AqKkjHJL6SR2wTTW",
        "avatar_key": "AqKkjHJL6SR2wTTW",
        "profile_cover": "https://w.wallhaven.cc/full/kw/wallhaven-kw9m1m.jpg",
        "online": 1,
        "rank": {
          "hidden": 1
        },
        "vip": 1,
        "games": 380,
        "games_wins": 170,
        "xp": 101880,
        "xp_level": 82,
        "moderator": 1,
        "superadmin": 1
      },
      {
        "user_id": 167,
        "nick": "LizaSai",
        "nicks_old": [],
        "gender": 0,
        "avatar": "https://pp.vk.me/c624131/v624131553/31aad/phYHVNrfub8.jpg",
        "rank": {
          "hidden": 1
        },
        "games": 10,
        "games_wins": 1,
        "xp": 0,
        "xp_level": 1
      },
      {
        "user_id": 3,
        "nick": "Lana",
        "nicks_old": [],
        "gender": 1,
        "avatar": "https://pp.vk.me/c637623/v637623553/15123/lPhI-fQ2N0I.jpg",
        "profile_cover": "https://pp.vk.me/c637226/v637226553/15695/kSjqHaSreA8.jpg",
        "rank": {
          "hidden": 1
        },
        "vip": 1,
        "games": 790,
        "games_wins": 243,
        "xp": 32903,
        "xp_level": 43
      }
    ]
  }
}
```
