
# auth.signin

<%- include('../../../includes/auth/not-applicable.md') %>

Авторизует пользователя в системе по адресу электронной почты и паролю.
В большинстве случаев вы не сможете автоматически пройти авторизацию, поскольку сервер будет отвечать кодом `8 Captcha needed`.

<aside warning>

Этот метод предназначен для авторизации пользователей в приложениях, а не на внешних веб-сайтах. Для авторизации пользователя Monopoly One на внешнем веб-сайте используйте [oAuth](/oauth/intro).

</aside>

## Параметры

<<< PARAMETERS
email: string [REQUIRED]
Адрес электронной почты пользователя.
<<<
password: string [REQUIRED]
Пароль пользователя.
Note: Пароль не может быть короче 10 символов.
<<<

## Результат

Если у пользователя **не настроена** двухфакторная аутентификация, то метод возвращает объект [`Session`](/objects/Session).

Если у пользователя **настроена** двухфакторная аутентификация, то метод возвращает ключ TOTP сессии `totp_session_token`, который действителен в течение 5 минут. Для создания сессии предоставьте TOTP код в метод [auth.totpVerify](/api/http/auth.totpVerify).

## Коды ошибок

<%- include('../../../includes/errors/head.md') -%>
<%- include('../../../includes/errors/412.md') -%>

# MARK: Examples

## Request

POST /api/auth.signin

```bash
curl -X POST "https://monopoly-one.com/api/auth.signin" \
     -d email="example@example.com" \
     -d password="deadbeef-0ff1ce"
```

## Ответ

однофакторная аутентификация

```json
{
  "code": 0,
  "data": {
    "user_id": 1234567890,
    "access_token": "1F27oDIn2oco3nj20SbmbQY6YqWrwg8r1HCJ",
    "expires_in": 86400,
    "expires": 86400,
    "refresh_token": "AXKiek3WaslNgCZb2360Y_FWu0HoCVt3folivJEDVPA6w2IuK3_ybUEZS6P63eg8-5OffFiO2tRFmr9_rEIib9Y8pLxzvpstcoBWznaU-NCBzc8zh7eQX46sRxUXlE3CqNY8UxPZpCrgVY57GIyi68M"
  }
}
```

двухфакторная аутентификация

```json
{
  "code": 0,
  "data": {
    "totp_session_token": "Ack_r_K4CV3lB1-OYE2Tp539CO8XQdpQe2vZlHu8e93qgeAwk-441r5HmzhH6nHQRne0zxLSOdOCIwKTleWUwPinwMTuukgZ7FAdx5sg2jRT"
  }
}
```
