
# Патч авторизации

<%- include('../../../includes/patch-upcoming.md') %>

## Введение объекта [`Session`](/objects/Session)

| Затронутые методы                            |
| -------------------------------------------- |
| [auth.signin](/api/http/auth.signin)         |
| [auth.totpVerify](/api/http/auth.totpVerify) |
| [bots.getToken](/api/http/bots.getToken)     |

Ранее при авторизации мы возвращали объекты с полями `access_token`, `refresh_token` и `expires`. Теперь же мы возвращаем объект [`Session`](/objects/Session), в котором поле `expires` переименовано в `expires_in`, но остальные поля остаются неизменными.

<aside info>
    В целях обеспечения совместимости некоторое время возвращаться будут оба поля.
</aside>

## Обновление TOTP

| Затронутые методы                            |
| -------------------------------------------- |
| [auth.signin](/api/http/auth.signin)         |
| [auth.totpVerify](/api/http/auth.totpVerify) |

- Поле `totp_session_id` переименовано в `totp_session_token`.
- Поле `token` переименовано в `totp_code`.

<%- include('../../../includes/compatibility-no.md') %>
