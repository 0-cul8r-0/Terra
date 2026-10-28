# ЛР8 — проверка PostgreSQL

Вариант 11 — работа с клиентской базой.

В репозитории находится небольшой тест для проверки подключения к PostgreSQL и выполнения SQL-запросов.

## Что лежит в проекте

`db/smoke_test.sql` — проверочный SQL-скрипт.

`scripts/check-postgres.ps1` — запуск проверки из PowerShell.

После успешного запуска создаётся файл `evidence/smoke-test.txt` с результатом выполнения.

## Перед запуском

Нужен установленный PostgreSQL 17.

Создать базу данных:

```sql
CREATE DATABASE remtechservice_lr8_konokhov;
```

Открыть PowerShell в папке проекта и задать параметры подключения:

```powershell
$env:PGHOST="localhost"
$env:PGPORT="5432"
$env:PGDATABASE="remtechservice_lr8_konokhov"
$env:PGUSER="postgres"
$env:PGPASSWORD="ваш_пароль"
```

## Запуск проверки

```powershell
.\scripts\check-postgres.ps1
```

Скрипт подключается к БД, создаёт тестовую схему и таблицу, добавляет контрольную запись и считывает её обратно.

Если всё работает, в результате будет строка:

```text
LR8 connection OK
```

Вывод проверки сохраняется в `evidence/smoke-test.txt`.
