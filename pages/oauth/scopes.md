
# Права доступа OAuth

| Название | Scope | Описание |
| --- | --- | --- |
| offline | **+1** | После предоставления доступа ваше приложение получит `refresh_token`, и сможет работать от имени пользователя без ограничения по времени. |
| games | **+2** | Вы сможете запрашивать историю игр пользователя. <br> **Доступные методы**: [games.my](/api/games.my). |
| stat | **+8** | Вы сможете просматривать прогресс сезонного пропуска пользователя (включая баланс токенов), его список заданий и его положение в топе недели. <br> **Доступные методы**: [missions.get](/api/missions.get), [seasonpass.get](/api/seasonpass.get), [users.getTopWeek](/api/users.getTopWeek). |