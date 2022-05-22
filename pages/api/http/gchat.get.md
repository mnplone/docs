
# gchat.get

<%- include('../../../includes/auth/not-applicable.md') %>

Получает сообщения из общего чата.

## Параметры

Этот метод не принимает параметров.

## Результат

Возвращает `dictionary<string, any>` со следующими параметрами:

<<< PARAMETERS
messages: list<[GchatMessage](/objects/GchatMessage)>
Сообщения в общем чате в порядке их появления.
<<<
status: dictionary<string, boolean>
Информация о статусе общего чата:
`closed` — если `true`, то общий чат закрыт написания сообщений;
`slowmode` — если `true`, то общий чат находится в медленном режиме (ограничение частоты отправки сообщений одним пользователем);
`emoteonly` — если `true`, то в общий чат можно писать только сообщения, полностью состоящие из эмотиконов Monopoly One.
<<<
users: list<[User](/objects/User)>?
Данные о пользователях, встречающихся в сообщениях.
Пользователи предоставляются в формате `short`.
<<<
item_protos: list<[Item](/objects/Item)>?
Данные о прототипах предметов, встречающихся в сообщениях.
Прототипы предметов предоставляются в формате `short`.
<<<

# MARK: Examples

## Request

GET /api/gchat.get

```bash
curl https://monopoly-one.com/api/gchat.get
```

## Ответ

```json
{
  "code": 0,
  "data": {
    "messages": [
      {
        "type": 1,
        "user_id": 1,
        "text": "hello @2 Bottle",
        "msg_id": "DHIKfl9AAAI",
        "ts": 1637597191,
        "user_ids_mentioned": [
          2
        ]
      },
      {
        "type": 3,
        "user_id": 2,
        "user_id_receiver": 3,
        "item_proto_id": 213,
        "msg_id": "DHINhTYAAAE",
        "ts": 1637597984
      },
      {
        "type": 4,
        "user_id": 4,
        "item_proto_ids": [
          57,
          489
        ],
        "msg_id": "DHIRKv8AAAE",
        "ts": 1637598941
      },
      {
        "type": 2,
        "user_id": 1,
        "case_item_proto_id": 50,
        "drop_item_proto_id": 49,
        "msg_id": "DHIRsWeAAAE",
        "ts": 1637599078
      }
    ],
    "status": {
      "closed": false,
      "slowmode": false,
      "emoteonly": false
    },
    "users": [
      {
        "user_id": 1,
        "domain": "kirick",
        "approved": 1,
        "nick": "kirick",
        "gender": 0,
        "avatar": "https://i.dogecdn.wtf/i8hJU5NdD9p06Mse",
        "avatar_key": "i8hJU5NdD9p06Mse",
        "online": 1,
        "rank": {
          "hidden": 1
        },
        "vip": 1,
        "moderator": 1,
        "superadmin": 1
      },
      {
        "user_id": 4,
        "nick": "Егор",
        "gender": 0,
        "avatar": "https://i.dogecdn.wtf/wxEpEiovduvcXadQ",
        "avatar_key": "wxEpEiovduvcXadQ",
        "rank": {
          "hidden": 1
        },
        "moderator": 1
      },
      {
        "user_id": 2,
        "domain": "anny",
        "nick": "AnnyPierce",
        "gender": 1,
        "avatar": "https://d1.dogecdn.wtf/547667302787711014/5d361198.jpg",
        "rank": {
          "hidden": 1
        },
        "moderator": 1
      },
      {
        "user_id": 3,
        "nick": "Lana",
        "gender": 1,
        "avatar": "https://pp.vk.me/c624722/v624722027/1b983/7kxvV0uejEI.jpg",
        "rank": {
          "hidden": 1
        }
      }
    ],
    "item_protos": [
      {
        "item_proto_id": 50,
        "type": 2,
        "image": "https://m1.dogecdn.wtf/things/case-jupiter.png",
        "title": "Кейс «Юпитер»",
        "description": "Этот контейнер содержит весьма ценные и совершенно новые карточки, а так же очень редкий Спиннер.",
        "quality_id": 1
      },
      {
        "item_proto_id": 49,
        "type": 4,
        "image": "https://m1.dogecdn.wtf/things/spinner.png",
        "title": "Спиннер",
        "description": "Во время Второй мировой войны не хватало материалов, чтобы сделать кубики для коробочной версии «Монополии», поэтому вместо кубиков решили использовать такой спиннер.",
        "quality_id": 4
      },
      {
        "item_proto_id": 57,
        "type": 6,
        "image": "https://m1.dogecdn.wtf/tickets/vip-month.svg",
        "title": "VIP-пропуск на месяц",
        "description": "Этот пропуск можно активировать, продлив свой VIP-статус на один месяц.\nVIP-статус даёт вам расширенные настройки при создании игры, а так же увеличивает шанс на выпадение предметов после игры.",
        "quality_id": 2
      },
      {
        "item_proto_id": 489,
        "type": 4,
        "image": "https://m1.dogecdn.wtf/dices/dicesbox5/vangogh.png",
        "title": "Кубики «Ван Гог»",
        "description": "",
        "quality_id": 5
      },
      {
        "item_proto_id": 213,
        "type": 6,
        "image": "https://m1.dogecdn.wtf/things/cake.png",
        "title": "Кусочек торта",
        "description": "Съев этот праздничный торт, вы присоединитесь к празднику и получите в подарок особый значок, VIP на три дня, а так же новый Королевский кейс и ключ к нему.\nВыпуск 2015 года. Срок годности не ограничен.",
        "quality_id": 1
      }
    ]
  }
}
```
