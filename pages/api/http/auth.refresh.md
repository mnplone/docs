
# auth.refresh

<%- include('../../../includes/auth/not-applicable.md') %>

Обменивает `refresh_token` на новую сессию.

## Параметры

<<< PARAMETERS
refresh_token: string [REQUIRED]
Ключ обновления авторизации.
<<<

## Результат

Возвращает объект [`Session`](/objects/Session).

# MARK: Examples

## Request

POST /api/auth.refresh

```bash
curl -X POST "https://monopoly-one.com/api/auth.refresh" \
     -d refresh_token="AVS16uIEblEFpQkhI7fCKdwDC70FQeFwhn860896vIksEK9znq3j9JmNSMqfrbR7eIqtgAxXIGcOXbpVZV8jVKcQjgFx_Pt5q6LIsI-9wzVLt65LOYTZ3M1JldWIeS4j-T-u0WbHCAhqZCl1bkX42Qs"
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
