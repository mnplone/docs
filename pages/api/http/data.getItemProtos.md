
# data.getItemProtos

<%- include('../../../includes/auth/not-applicable.md') %>

Возвращает прототипы предметов.

## Параметры

<<< PARAMETERS
item_proto_ids: set<uint> [REQUIRED]
Идентификаторы прототипов предметов.
<<<
add_legacy: bit? = 0
Встраивать ли в объекты [`Item`](/objects/Item) параметры устаревшего объекта [`Thing`](/objects/Thing).
<<<
add_metadata: bit? = 1
Добавить ли в ответ дополнительные данные, связанные с прототипами предметов.
<<<

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

GET /api/data.getItemProtos

```bash
curl https://monopoly-one.com/api/data.getItemProtos?item_proto_ids=50,51,79
```

## Ответ

```json
{
  "code": 0,
  "data": {
    "item_protos": [
      {
        "item_proto_id": 50,
        "type": 2,
        "image": "https://m1.dogecdn.wtf/things/case-jupiter.png",
        "title": "Кейс «Юпитер»",
        "description": "Этот контейнер содержит весьма ценные и совершенно новые карточки, а так же очень редкий Спиннер.",
        "quality_id": 1,
        "collection_id": 4,
        "prices": {
          "quick_sell": 0.3
        },
        "key_item_proto_id": 51,
        "drop": [
          {
            "item_proto_id": 42
          },
          {
            "item_proto_id": 43
          },
          {
            "item_proto_id": 44
          },
          {
            "item_proto_id": 45
          },
          {
            "item_proto_id": 46
          },
          {
            "item_proto_id": 47
          },
          {
            "item_proto_id": 48
          },
          {
            "item_proto_id": 111,
            "is_secondary": 1
          },
          {
            "item_proto_id": 112,
            "is_secondary": 1
          },
          {
            "item_proto_id": 113,
            "is_secondary": 1
          },
          {
            "item_proto_id": 114,
            "is_secondary": 1
          },
          {
            "item_proto_id": 115,
            "is_secondary": 1
          },
          {
            "item_proto_id": 116,
            "is_secondary": 1
          },
          {
            "item_proto_id": 117,
            "is_secondary": 1
          },
          {
            "item_proto_id": 49,
            "is_rare": 1
          }
        ]
      },
      {
        "item_proto_id": 51,
        "type": 3,
        "image": "https://m1.dogecdn.wtf/keys/jupiter.svg",
        "title": "Ключ от кейса «Юпитер»",
        "description": "Этот ключ открывает только кейс «Юпитер».",
        "quality_id": 1,
        "prices": {
          "buy": 33
        },
        "case_item_proto_ids": [
          50
        ]
      },
      {
        "item_proto_id": 79,
        "type": 0,
        "image": "https://i.dogecdn.wtf/pHC3RiGLNEflgsK0",
        "title": "axiom",
        "description": "Axiom — китайский производитель электроники, известный прежде всего своими смартфонами и товарами для «умного дома».",
        "monopoly_id": 8,
        "quality_id": 5
      }
    ],
    "collections": [
      {
        "collection_id": 4,
        "title": "Коллекция «Юпитер»"
      }
    ]
  }
}
```
