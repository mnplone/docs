
# data.searchItemProtos

<%- include('../../../includes/auth/not-applicable.md') %>

Возвращает прототипы предметов по заданным параметрам поиска.

## Параметры

<<< PARAMETERS
type: set<uint>
Идентификаторы типов.
<<<
quality_id: set<uint>
Идентификаторы классов.
<<<
collection_id: set<uint>
Идентификаторы колллекций.
<<<
group_id: set<uint>
Идентификаторы монополий (`monopoly_id`) или групп стикеров (`sticker_group_id`).
<<<
add_legacy: bit? = 0
Встраивать ли в объекты [`Item`](/objects/Item) параметры устаревшего объекта [`Thing`](/objects/Thing).
<<<
add_metadata: bit? = 1
Добавить ли в ответ дополнительные данные, связанные с прототипами предметов.
<<<
<%- include('../../../includes/parameters/offset.md') -%>
<%- include('../../../includes/parameters/count.md') -%>

## Результат

Возвращает `dictionary<string, any?>` со следующими параметрами:

<<< PARAMETERS
item_protos: list<[Item](/objects/Item)>
Данные о прототипах предметов.
<<<
collections: list<dictionary<string, any>>?
Данные о коллекциях, которые упомянуты в параметре `item_protos`. Каждый объект состоит из:
`collection_id: uint` — идентификатор коллекции;
`title: string` — название коллекции.
<<<

# MARK: Examples

## Request

GET /api/data.searchItemProtos

```bash
curl https://monopoly-one.com/api/data.searchItemProtos?quality_id=1&type=3&count=3
```

## Ответ

```json
{
  "code": 0,
  "data": {
    "item_protos": [
      {
        "item_proto_id": 51,
        "type": 3,
        "image": "https://m1.dogecdn.wtf/keys/jupiter.svg",
        "title": "Ключ от кейса «Юпитер»",
        "description": "Этот ключ открывает только кейс «Юпитер».",
        "quality_id": 1,
        "prices": {
          "buy": 39
        },
        "case_item_proto_ids": [
          50
        ]
      },
      {
        "item_proto_id": 71,
        "type": 3,
        "image": "https://m1.dogecdn.wtf/keys/dicesbox.svg",
        "title": "Ключ от коробочки с кубиками",
        "description": "Этот ключ откроет любую коробочку с кубиками.",
        "quality_id": 1,
        "prices": {
          "buy": 39
        },
        "case_item_proto_ids": [
          70,
          129,
          170,
          304,
          491,
          742,
          820
        ]
      },
      {
        "item_proto_id": 81,
        "type": 3,
        "image": "https://m1.dogecdn.wtf/things/key-bright.png",
        "title": "Ключ от Яркого кейса",
        "description": "Этот ключ открывает только Яркий кейс.",
        "quality_id": 1,
        "prices": {
          "buy": 39
        },
        "case_item_proto_ids": [
          80
        ]
      }
    ],
    "collections": []
  }
}
```
