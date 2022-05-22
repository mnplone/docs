
# Объект `Item` и друзья

17 ноября 2021.

Мы готовимся переделать объект [`Thing`](/objects/Thing) в объект [`Item`](/objects/Item). Релизом будут затронуты следующие задокументированные ранее методы:

- [inventory.get](/api/http/inventory.get);
- [gchat.get](/api/http/gchat.get).

Методы `trades.*`, также работающие с объектами [`Thing`](/objects/Thing), пока не будут переведены в режим совместимости с объектом [`Item`](/objects/Item).

В методе [inventory.get](/api/http/inventory.get) мы постараемся сохранить новые параметры наравне со старыми (объекты [`Item`](/objects/Item) и [`Thing`](/objects/Thing) будут объединены).
Мы рекоменуем уже сейчас подготовить код к взаимодействию в первую очередь с параметрами объекта [`Item`](/objects/Item).

## Изменения в описания предметов

### Изменённые параметры

| Параметр&nbsp;объекта&nbsp;[`Thing`](/objects/Thing) | Параметр&nbsp;объекта&nbsp;[`Item`](/objects/Item) | Описание изменений |
| --- | --- | --- |
| `thing_id` | `item_id` | |
| `thing_prototype_id` | `item_proto_id` | |
| `thing_proto_status` | `item_proto_status` | Не будет передаваться, если значение равно `0`. |
| `thing_type` | `type` | |
| `group` | `monopoly_id` | |
| `sticker_group` | `sticker_group_id` | |
| `quality` | `quality_id` | |
| `collection` | `collection_id` | Не будет передаваться, если предмет не принадлежит ни к одной коллекции (ранее передавалось значение `-1`). |
| `twin_thing_prototype_id` | `twin_item_proto_ids` | |
| `owned_time` | `ts_owned` | |
| `can_give` | `ts_can_trade` | |
| `can_sell` | `ts_can_sell` | |
| `delete_price` | `prices.quick_sell` | Параметр перемещён в объект `prices`. |
| `can_void` | `can_delete` | |
| `can_be_upgraded` | `can_craft` | Не будет передаваться, если значение равно `0`. |
| `buy_cost` | `prices.buy` | Параметр перемещён в объект `prices`. |
| `buy_costs_by_count` | `prices.buy` | Параметр перемещён в объект `prices`. |
| `key` | `key_item_proto_id` | |
| `cases` | `case_item_proto_ids` | |
| `drop` | `drop` | В объекте будут передаваться все предметы, которые могут выпасть из кейса (ранее вместо списка редких предметов выдавался псевдо-предмет `rare:1`, а предметы с копилками не передавались вообще). |
| `owners_history` | `previous_owners_user_ids` | |
| `uses_left` | `uses.left` | Параметр перемещён в объект `uses`. |
| `uses_origin` | `uses.origin` | Параметр перемещён в объект `uses`. |

### Удалённые параметры

| Параметр&nbsp;объекта&nbsp;[`Thing`](/objects/Thing) | Описание изменений |
| --- | --- |
| `user_id` | Поскольку у нас нет работы с предметами вне контекста игрока, то мы удалили этот параметр. Вы должны самостоятельно понимать, чей предмет вы обрабатываете. |

### Добавленные параметры

| Параметр&nbsp;объекта&nbsp;[`Item`](/objects/Item) | Описание изменений |
| --- | --- |
| `item_ids` | В будущем мы будем группировать одинаковые предметы в один, чтобы не отдавать по тысяче раз одинаковые кейсы из инвентаря. В этом параметре будут перечислены все `item_id` сгруппированных предметов. |

## Изменения [inventory.get](/api/http/inventory.get)

Параметр запроса `add_user_info` будет называться `add_user`.

Параметр ответа `user_info` будет называться `user`.

Обратная совместимость пока останется.

## Новый метод [data.getItemProtos](/api/http/data.getItemProtos)

Метод [data.getItemProtos](/api/http/data.getItemProtos) заменит собой метод [data.getThingPrototypes](/api/http/data.getThingPrototypes), который продолжит работать, но будет считаться устаревшим.

## Удаление параметров ответа `thing_types` и `qualities`

Методы [data.getItemProtos](/api/http/data.getItemProtos) и [inventory.get](/api/http/inventory.get) более не будут возвращать в качестве дополнительных данных поля `thing_types` и `qualities`. Эти списки чрезвычайно малы и крайне редко обновляются, поэтому не имеет смысла передавать их по сети.
