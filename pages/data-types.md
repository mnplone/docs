
# Типы данных

В данной документации мы описываем типы данных в следующем формате:

| Формат           | Описание                                                                 |
| ---------------- | ------------------------------------------------------------------------ |
| `type`           | объект типа `type`                                                       |
| `type1 \| type2` | объект типа `type1` или `type2`                                          |
| `type?`          | объект типа `type` <br> значение может отсутствовать                     |
| `type? = value`  | объект типа `type` <br> при отсутствии значения считается равным `value` |

## Общие типы

| Тип                  | Описание                                                                            |
| -------------------- | ----------------------------------------------------------------------------------- |
| `any`                | любой тип данных                                                                    |
| `boolean`            | `true` или `false`                                                                  |
| `bit`                | тот же `boolean`, но `true` обозначается числом `1`, а `false` — числом `0`         |
| `string`             | строка                                                                              |
| `int`                | целое число в диапазоне от `-9007199254740991` до `9007199254740991`                |
| `uint`               | целое число в диапазоне от `0` до `9007199254740991`                                |
| `double`             | число с плавающей точкой двойной точности                                           |
| `list<T>`            | упорядоченный список неуникальных значений (массив) типа `T`                        |
| `set<T>`             | неупорядоченный список уникальных значений (множество) типа `T`                     |
| `dictionary<T1, T2>` | неупорядоченный словарь (объект) значений типа `T2`, хранящихся по ключам типа `T1` |

## Дополнительные типы

Эти типы описывают стандартные объекты, использующиеся в API.

| Тип                                     | Описание                              |
| --------------------------------------- | ------------------------------------- |
| [`GchatMessage`](/objects/GchatMessage) | сообщение в общем чате                |
| [`Item`](/objects/Item)                 | предмет инвентаря                     |
| [`ItemVariant`](/objects/ItemVariant)   | облик предмета инвентаря              |
| [`Session`](/objects/Session)           | сессия (данные авторизации)           |
| [`Thing`](/objects/Thing)               | предмет инвентаря (устаревший формат) |
| [`Trade`](/objects/Trade)               | предложение обмена                    |
| [`User`](/objects/User)                 | пользователь                          |
