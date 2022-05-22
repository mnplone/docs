
# inventory.get

<%- include('../../../includes/auth/optional.md') %>

Возвращает информацию об инвентаре пользователя.

## Параметры

<<< PARAMETERS
user_id: uint? | string?
Идентификатор или домен пользователя, друзья которого запрашиваются.
Note: По умолчанию равен идентификатору текущего пользователя.
<<<
include_stock: bit? = 0
Возвращать ли предметы стокового класса (`quality_id = 0`).
Note: Этот параметр применяется только для инвентаря текущего пользователя.
<<<
order: string? = "time"
Правило сортировки предметов:
`time` — по времени получения предметов (от большего к меньшему);
`quality` — по классу (от большего к меньшему).
<<<
count: uint = Infinity
Количество предметов, которые надо вернуть.
<<<
add_user: bit? = 0
Вернуть ли данные о самом пользователе.
<<<
add_user_info: bit? = 0 [DEPRECATED]
Вернуть ли данные о самом пользователе.
Note: Используйте вместо этого параметр `add_user`.
<<<
add_equipped: string?
Возвращать ли список используемых предметов на поле (для карточек, генераторов чисел и насмешек) и на профиле (для значков):
`array` — вернёт идентификаторы используемых предметов в виде списка;
`tree` — вернёт подробную информацию о позициях используемых предметов.
Note: Этот параметр применяется только для инвентаря текущего пользователя.
<<<
add_legacy: bit? = 1
Встраивать ли в объекты [`Item`](/objects/Item) параметры устаревшего объекта [`Thing`](/objects/Thing).
Note: Этот параметр включен по умолчанию для совместимости старых клиентов.
<<<
shrink: bit? = 0 [EXPERIMENTAL]
Сжимать ли несколько одинаковых предметов в один для уменьшения размера ответа.
Note: На данный момент мы рекомендуем использовать этот параметр только для тестов.
<<<

## Результат

Возвращает `dictionary<string, any?>` со следующими параметрами:

<<< PARAMETERS
count: uint
Общее количество предметов в инвентаре.
<<<
items: list<[Item](/objects/Item)>
Список предметов в инвентаре **без режима совместимости**.
Note: Возвращается при параметре запроса `add_legacy = 0`.
<<<
things: list<[Item](/objects/Item)> [DEPRECATED]
Список предметов в инвентаре **в режиме совместимости**, когда каждый объект [`Item`](/objects/Item) включает в себя поля устаревшего объекта [`Thing`](/objects/Thing).
Note: Возвращается при параметре запроса `add_legacy = 1`.
<<<
collections: list<dictionary<string, any>>
Данные о коллекциях, которые упомянуты в предметах инвентаря. Каждый объект состоит из:
`collection_id: uint` — идентификатор коллекции;
`id: uint?` — идентификатор коллекции (**устаревший параметр**, передаётся только при параметре запроса `add_legacy = 1`);
`title: string` — название коллекции.
<<<
thing_types: list<dictionary<string, any>>? [DEPRECATED]
Данные о типах предметов, которые упомянуты в предметах инвентаря. Каждый объект состоит из:
`id: uint` — идентификатор типа предмета;
`title: string` — название типа предмета.
Note: Возвращается при параметре запроса `add_legacy = 1`.
<<<
qualities: list<dictionary<string, any>>? [DEPRECATED]
Данные о классах предметов, которые упомянуты в предметах инвентаря. Каждый объект состоит из:
`id: uint` — идентификатор класса;
`title: string` — название класса;
`coeff_rent: double` — множитель аренды для карт этого класса.
Note: Возвращается при параметре запроса `add_legacy = 1`.
<<<
item_ids_equipped: set<uint>?
Список идентификаторов предметов, которые используются пользователем.
Note: Возвращается при параметре запроса `add_equipped = "array"`.
<<<
equipped: dictionary<string, any?>?
Подробная информация об используемых пользователем предметах.
Note: Возвращается при параметре запроса `add_equipped = "tree"`.
<<<
user: [User](/objects/User)?
Данные о пользователе, чей инвентарь был запрошен.
Note: Возвращается при параметре запроса `add_user = 1`.
<<<
user_info: [User](/objects/User)? [DEPRECATED]
Данные о пользователе, чей инвентарь был запрошен.
Note: Возвращается при параметре запроса `add_user_info = 1`.
<<<

## Коды ошибок

<%- include('../../../includes/errors/head.md') -%>
<%- include('../../../includes/errors/101.md') -%>
<%- include('../../../includes/errors/701.md') -%>

# MARK: Examples

## Request

GET /api/inventory.get

```bash
curl https://monopoly-one.com/api/inventory.get?user_id=1023502&add_legacy=0&add_user=1
```

## Ответ

```json
{
  "code": 0,
  "data": {
    "count": 3,
    "items": [
      {
        "item_id": 19768,
        "item_proto_id": 51,
        "type": 3,
        "image": "https://m1.dogecdn.wtf/keys/jupiter.svg",
        "title": "Ключ от кейса «Юпитер»",
        "description": "Этот ключ открывает только кейс «Юпитер».",
        "quality_id": 1,
        "prices": {
          "buy": 33
        },
        "ts_owned": 1636205208,
        "case_item_proto_ids": [
          50
        ]
      },
      {
        "item_id": 13070,
        "item_proto_id": 543,
        "type": 6,
        "image": "https://m1.dogecdn.wtf/tickets/m1cup-2017-fall.png",
        "title": "Билет на M1 Cup, осень 2017",
        "description": "Активировав этот пропуск, вы станете полноправным зрителем осеннего турнира M1 Cup 2017. В память о турнире вы получите значок зрителя, а во время просмотра матчей этого турнира у вас будет шанс на выпадение сувенирных наборов Zero, Uno, Deux и Tre.",
        "quality_id": 1,
        "ts_owned": 1510080272
      },
      {
        "item_id": 13062,
        "item_proto_id": 550,
        "type": 1,
        "image": "https://m1.dogecdn.wtf/cases/trnmnt/m1cup/2017/fall/uno.png",
        "title": "Сувенирный набор Uno",
        "description": "Набор Uno объединяет в себе карточки трёх самых лучших монополий — «Рестораны», «Отели» и «Электроника».",
        "quality_id": 1,
        "collection_id": 1,
        "ts_owned": 1509980093,
        "drop": [
          {
            "item_proto_id": 25
          },
          {
            "item_proto_id": 26
          },
          {
            "item_proto_id": 27
          },
          {
            "item_proto_id": 29
          },
          {
            "item_proto_id": 30
          },
          {
            "item_proto_id": 31
          },
          {
            "item_proto_id": 33
          },
          {
            "item_proto_id": 34
          },
          {
            "item_proto_id": 35
          },
          {
            "item_proto_id": 28
          },
          {
            "item_proto_id": 32
          },
          {
            "item_proto_id": 36
          },
          {
            "item_proto_id": 38
          },
          {
            "item_proto_id": 58
          }
        ]
      }
    ],
    "collections": [
      {
        "collection_id": 1,
        "title": "Коллекция «Uno»"
      }
    ],
    "user": {
      "user_id": 1023502,
      "nick": "Alfa",
      "nicks_old": [],
      "gender": 0,
      "avatar": "https://i.dogecdn.wtf/wxEpEiovduvcXadQ",
      "avatar_key": "wxEpEiovduvcXadQ",
      "rank": {
        "hidden": 1
      },
      "games": 9,
      "games_wins": 2,
      "xp": 38,
      "xp_level": 1,
      "friendship": 0
    }
  }
}
```
