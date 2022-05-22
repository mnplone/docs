
# inventory.craft

<%- include('../../../includes/auth/required.md') %>

Крафтит из десяти предметов одного класса предмет классом выше.

## Параметры

<<< PARAMETERS
item_ids: set<uint> [REQUIRED]
   Идентификаторы предметов, отправляемых в крафт.

## Результат

Возвращает скрафченный предмет типа [`Item`](/objects/Item).

## Коды ошибок

<%- include('../../../includes/errors/head.md') -%>
| **603** | Какой-либо из переданных предметов невозможно использовать в крафте. |
| **605** | Предметы должны быть одного типа и класса. |
<%- include('../../../includes/errors/624.md') -%>

# MARK: Examples

## Request

POST /api/inventory.craft

```bash
curl -X POST "https://monopoly-one.com/api/inventory.craft" \
     -d item_ids="19520,19597,19519,19148,19146,19140,19138,16460,16459,16458"
```

## Ответ

```json
{
  "code": 0,
  "data": {
    "item": {
      "item_id": 19918,
      "item_proto_id": 788,
      "type": 0,
      "image": "https://i.dogecdn.wtf/uoBwxWRGDtfeweFl",
      "title": "von",
      "description": "",
      "monopoly_id": 6,
      "quality_id": 3,
      "collection_id": 40,
      "twin_item_proto_ids": [
        796
      ],
      "ts_owned": 1637658947,
      "can_craft": 1
    }
  }
}
```
