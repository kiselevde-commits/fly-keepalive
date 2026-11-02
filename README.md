# fly-keepalive

Пингер для бота **telegram-sarcasm-bot** на Fly.io (trial-аккаунт без карты).

Trial гасит машину через 5 минут после старта, но любой HTTP-запрос на
`https://telegram-sarcasm-bot.fly.dev/healthz` поднимает её заново
(`auto_start_machines = true`). Этот репозиторий делает такие запросы по
расписанию GitHub Actions и не зависит ни от чьего компьютера.

- [.github/workflows/ping.yml](.github/workflows/ping.yml) — запуск каждые 5 минут,
  внутри запуска 5 пингов с шагом 55 секунд (расписание GitHub часто опаздывает).
- [.github/workflows/heartbeat.yml](.github/workflows/heartbeat.yml) — раз в неделю
  делает пустой коммит, чтобы GitHub не отключил расписание после 60 дней простоя.

Репозиторий публичный намеренно: минуты Actions для публичных репозиториев
бесплатны. Секретов здесь нет — только публичный адрес healthz.

Выключить: удалить репозиторий или отключить оба workflow во вкладке Actions.
