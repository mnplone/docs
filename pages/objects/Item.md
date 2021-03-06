
# Объект `Item`

Тип `dictionary<string, any?>`.

Описывает предмет из инвентаря.

Данные о каждом предмете состоят из двух частей:
1. параметров прототипа (`item_proto`), которые одинаковы для всех вещей одного прототипа (например, все кубики «Дракон» имеют одинаковое название и эксклюзивный класс);
2. параметров предмета (`item`), уникальных именно для него (время получения, автограф и так далее).

## Параметры прототипа

### Короткий формат (`short`)

<<< PARAMETERS
item_proto_id: uint
Идентификатор прототипа предмета.
<<<
item_proto_status: uint? = 0
Статус прототипа предмета:
`0`: у предметов этого прототипа нет ограничений;
`1`: предметы этого прототипа нельзя передавать и продавать.
<<<
type: uint
Тип предмета:
`0` — карточка;
`1` — подарочный набор;
`2` — кейс;
`3` — ключ;
`4` — генератор чисел;
`5` — значок;
`6` — пропуск (одноразовый предмет);
`7` — подписка (многоразовый предмет);
`8` — насмешка;
`9` — стикер.
<<<
image: string
Ссылка на картинку прототипа предмета.
<<<
title: string
Название прототипа предмета.
<<<
description: string
Текстовое описание прототипа предмета.
<<<
quality_id: uint
Класс предмета:
`0` — стоковый (серый);
`1` — обыкновенный (голубой);
`2` — стандартный (синий);
`3` — особенный (фиолетовый);
`4` — высочайший (красный);
`5` — эксклюзивный (золотой).
<<<
moneybox: bit? = 0
Имеется ли у предметов этого прототипа копилка.
<<<
variants: list<[ItemVariant](/objects/ItemVariant)>?
Варианты (облики) предмета.
<<<

### Остальные форматы

Эти параметры добавляются к параметрам формата `short`.

<<< PARAMETERS
monopoly_id: uint?
Идентификатор монополии, к которой принадлежит карточка (`type=1`).
<<<
sticker_group_id: uint?
Идентификатор группы, к которой принадлежит стикер (`type=9`).
<<<
collection_id: uint?
Идентификатор коллекции, к которой принадлежит предмет.
<<<
twin_item_proto_ids: list<uint>?
Идентификаторы прототипов предметов, которые нельзя установить на поле вместе с предметом текущего прототипом.
<<<
prices: dictionary<string, any?>?
Цены, связанные с прототипом предмета. Объект с полями:
`buy: float?` — цена покупки одного предмета у сайта в «р.»;
`buy: dictionary<string, float>?` — цены покупки (значения словаря) одного предмета с разным количеством использований (ключи словаря) у сайта в «р.»;
`quick_sell: float?` — цена продажи одного предмета в систему в «р.».
<<<
key_item_proto_id: uint?
Идентификатор прототипа ключа (`type=3`), которым можно открыть данный кейс (`type=2`).
<<<
case_item_proto_ids: list<uint>?
Идентификаторы прототипов кейсов (`type=2`), которые можно открыть этим ключом (`type=3`).
<<<
drop: dictionary<string, any?>?
Список предметов, которые могут выпасть из этого кейса (`type=2`) или подарочного набора (`type=1`).
<<<
can_craft: bit? = 0
Можно ли предметы этого прототипа отправлять в крафт.
<<<

## Параметры предмета

<aside info>

Некоторые параметры предмета совпадают по названию с параметрами прототипа предмета. В этом случае параметры *предмета* замещают параметры *прототипа предмета*.

</aside>

### Короткий формат (`short`)

<<< PARAMETERS
item_id: uint
Идентификатор предмета.
<<<
item_ids: list<uint>?
Идентификаторы предметов, полностью идентичных текущему и потому сгруппированных в один для уменьшения размера ответа.
<<<
ts_owned: uint
Время, когда предмет был получен пользователем в инвентарь.
<<<
ts_can_trade: int?
Время, когда предмет будет доступен для передачи другим пользователям и для отправки в крафт. <br> Равен `-1`, если блокировка данных действий бессрочная.
<<<
ts_can_sell: int?
Время, когда предмет будет доступен для продажи в систему и на Маркете. <br> Равен `-1`, если блокировка данных действий бессрочная.
<<<
souvenir: string?
Сувенирная надпись на предмете.
<<<
autograph: dictionary<string, any?>?
Автограф. Содержит поля:
`user_id: uint` — идентификатор пользователя, автора автографа;
`text: string?` — текст автографа.
<<<
moneybox: dictionary<string, any>?
Данные о копилке на предмете.
Если это карточка (`type=0`), то содержит следующие поля:
`transactions: uint` — количество попаданий соперников на карточку;
`money_inside: uint` — сумма собранной аренды.
Если это генератор чисел (`type=4`), то содержит следующие поля:
`numbers: list<uint>` — количество сгенерированных чисел от 1 до 6.
Если это насмешка (`type=8`), то содержит следующие поля:
`count: uint` — количество обанкроченных соперников.
<<<
seed: string?
Зерно для алгоритма генерации текстуры предмета (обычно это текстуры кубиков типа «Роршах»).
<<<
variants: list<[ItemVariant](/objects/ItemVariant)>?
Варианты (облики) предмета.
<<<
xp_boost: uint?
Количество опыта, которое даст бустер опыта.
<<<

### Остальные форматы

Эти параметры добавляются к параметрам формата `short`.

<<< PARAMETERS
can_delete: bit? = 0
Может ли пользователь удалить предмет.
<<<
previous_owners_user_ids: list<uint>?
Идентификаторы пользователей, ранее владевших предметом.
<<<
uses: dictionary<string, uint?>?
Информация о количестве использований подписки (`type=7`). Содержит поля:
`left: uint` — количество раз, которые предмет можно использовать;
`origin: uint?` — количество раз, которые предмет можно было использовать изначально (данное поле отсутствует у очень старых предметов).
<<<
