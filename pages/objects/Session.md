
# Объект `Session`

Тип `dictionary<string, any?>`.

Описывает сессию.

## Параметры

<<< PARAMETERS
user_id: uint
Идентификатор пользователя.
<<<
access_token: string
Ключ авторизации.
<<<
expires_in: uint
Количество секунд, в течение которых действителен ключ авторизации.
<<<
expires: uint [DEPRECATED]
Количество секунд, в течение которых действителен ключ авторизации.
<<<
refresh_token: string?
Ключ обновления авторизации.
<<<
