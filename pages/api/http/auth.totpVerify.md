
# auth.totpVerify

<%- include('../../../includes/auth/not-applicable.md') %>

Завершает авторизацию, прерванную двухфакторной аутентификацией.

## Параметры

<<< PARAMETERS
totp_session_token: string [REQUIRED]
Ключ TOTP сессии.
<<<
code: string [REQUIRED]
Код двухфакторной аутентификации.
<<<

## Результат

Возвращает объект [`Session`](/objects/Session).

## Коды ошибок

<%- include('../../../includes/errors/head.md') -%>
<%- include('../../../includes/errors/412.md') -%>
<%- include('../../../includes/errors/413.md') -%>
<%- include('../../../includes/errors/414.md') -%>

# MARK: Examples

## Request

POST /api/auth.totpVerify

```bash
curl -X POST "https://monopoly-one.com/api/auth.totpVerify" \
     -d totp_session_token="hc0lECz0PEf9PmfwkehXp6y9FCRf1l7i4j6z" \
     -d code="123456"
```

## Ответ

```json
{
  "code": 0,
  "data": {
    "user_id": 1234567890,
    "access_token": "y6NSPZ3o43mtpXD7a2g5qq75gqMTd8Hmfj87",
    "expires_in": 86400,
    "expires": 86400,
    "refresh_token": "AQIArtrCjEY1L25_Y9qMUIUq66-JKIYYfmTJs68L0oOAuVTxPYDltdgQQQthYJuBL6yBJtOXM9b6t_shHoW9dA45NKhRGbkkHaaBpPpfD3uq0Wi8jYrlCNlxJ0zcbg1G8PbtDjuqnm4AlsvmdXW7jJ4"
  }
}
```
