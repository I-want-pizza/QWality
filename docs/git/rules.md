# Гайд по Git Flow

## 1. База
- **Main** - стабильная продакшен ветка (заливается только релизнутая версия)
- **Develop** - основная ветка для разработки (тут сливаются ветки с фичей)
- Поддерживающие ветки:
    - `feature/` - для новых функций
    - `release/` - для сращения фичей
    - `fix/` - для исправлений

## 2. Стандарт коммитов
`<type>(<scopre>): <subject> <body> <footer>`
- type: тип изменения (подробнее далее)
- scope: область применения _(необязательно)_
- subject: краткое описание изменений (пишется в повелительном наклонении: `Added something` - плохо, `Add something` - хорошо)
- body: тело коммита _(необязательно)_
- footer: код задачи из таск-трекера

**Пример:**
>fix(login): resolve 500 error on invalid credentials
> 
> Из-за того-то того-то не работало то-то то-то
> 
>Fixes: QW-45

**Типы:**
# Стандартные типы коммитов

| Тип        | Описание                                                    |
|------------|-------------------------------------------------------------|
| `feat`     | Новая функциональность                                      |
| `fix`      | Исправление бага                                            |
| `docs`     | Изменения документации                                      |
| `style`    | Изменения, не влияющие на логику                            |
| `refactor` | Рефакторинг кода                                            |
| `test`     | Тесты                                                       |
| `chore`    | Мелкие задачи, не связанные с новыми функциями или ошибками |
| `revert`   | откат на предыдущие коммиты                                 |


## 3. Детализация веток

### 3.1 Фичи (feature ветки)
**Название:** `feature/QW-[id]-[краткое-описание]` (например: `feature/user-profile`)
`id - это id задачи из таск-трекера`

**Правила:**
- Ответвляются от `develop`
- Мержатся обратно в `develop`
- Должны содержать атомарные изменения
- Удаляются после мержа

### 3.2 Релизы (release ветки)
**Название:** `release/[версия]` (например: `release/1.3.0`)

**Правила:**
- Ответвляются от `develop` **или** от `main`
- Мержатся в `develop` **или** от `main` соответственно
- Теги версий создаются только из релизных веток
- Удаляются после вливания

### 3.3 Фиксы (fix ветки)
**Название:** `fix/QW-[id]-[описание]` (например: `fix/login-security`)
`id - это id задачи из таск-трекера`

**Правила:**
- Ответвляются от `develop` **или** от `main`
- Мержатся в `develop` **или** от `main` соответственно
- Теги версий создаются только из релизных веток
- Удаляются после вливания