
# oauth.exchangeCode

<%- include('../../../includes/auth/not-applicable.md') %>

Завершает авторизацию [OAuth](/oauth/intro), обменивая `code` на сессию.

## Параметры

<<< PARAMETERS
app_id: uint
Идентификатор приложения.
<<<
app_secret: string
Секретный ключ приложения.
<<<
code: string
Параметр `code`, полученный после перехода пользователя по `redirect_uri`.
<<<
redirect_uri: string
Адрес, по которому пользователь был перенаправлен при предоставлении им доступа к аккаунту.
Note: в случае несовпадения `redirect_uri` в авторизации будет отказано.
<<<

## Результат

Возвращает объект [`Session`](/objects/Session).

## Коды ошибок

<%- include('../../../includes/errors/head.md') -%>
| **2001** | Параметр `code` некорректен либо устарел. |
| **2002** | Параметр `redirect_uri` не совпадает с тем, что был передан при авторизации. |
| **2003** | Секретный ключ приложения неверен. |
| **2004** | Приложения не существует. |
| **2005** | Приложение неактивно или заблокировано. |
| **2007** | Параметр `redirect_uri` некорректен. <br> В параметре `$.details` будет указана конкретная причина. |

# MARK: Examples

## Request

POST /api/oauth.exchangeCode

```bash
curl -X POST "https://monopoly-one.com/api/oauth.exchangeCode" \
     -d app_id="1" \
     -d app_secret="DEADBEEF" \
     -d code="1234567890" \
     -d redirect_uri="https://example.com/oauth/callback"
```

## Ответ

```json
{
  "code": 0,
  "data": {
    "user_id": 1234567890,
    "access_token": "y3NRXPecU4zoWLzdIh6q152i22RWYnol1tw2",
    "expires_in": 86400,
    "expires": 86400,
    "refresh_token": "AQVfoF0lWnQXBkyTWmmRV5F1jptv4Lm4FCByM5N1ZU1G5xCs7bzXpoEKMwDZzn__hhCJFRhyBvgb5ZK_ytRQ2EYUtc97sKngr22gGf8oFxoKs1HAnUANNu4Wv5S0bUAkQA",
  }
}
```
