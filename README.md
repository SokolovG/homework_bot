# Homework Status Bot

Telegram-бот для отслеживания статуса проверки домашних работ на Яндекс Практикуме. Бот автоматически проверяет статус домашней работы через API Практикума и отправляет уведомления в Telegram при изменении статуса.

## Функциональность

- Автоматическая проверка статуса домашней работы каждые 10 минут
- Мгновенные уведомления об изменении статуса работы:
  - Взята в проверку
  - Проверена и принята
  - Возвращена на доработку
- Логирование работы бота
- Уведомления об ошибках в Telegram

## Технологии

- Python 3.9+
- python-telegram-bot
- Python Requests
- dotenv

## Установка

1. Клонируйте репозиторий:
```bash
git clone git@github.com:ваш-аккаунт/homework_bot.git
cd homework_bot
```

2. Создайте и активируйте виртуальное окружение:
```bash
python -m venv venv
source venv/bin/activate
```

3. Установите зависимости:
```bash
pip install -r requirements.txt
```

## Настройка

1. Создайте файл `.env` в корневой директории проекта
2. Добавьте в него следующие переменные окружения:
```
PRACTICUM_TOKEN=<ваш_токен_практикума>
TELEGRAM_TOKEN=<токен_вашего_бота>
TELEGRAM_CHAT_ID=<ваш_chat_id>
```

Где взять токены:
- `PRACTICUM_TOKEN` можно получить на странице профиля в Практикуме
- `TELEGRAM_TOKEN` можно получить у @BotFather в Telegram
- `TELEGRAM_CHAT_ID` можно узнать у @userinfobot в Telegram

## Запуск

```bash
python homework.py
```

## Структура проекта

```
homework_bot/
├── homework.py         # Основной файл программы
├── exceptions.py       # Кастомные исключения
├── requirements.txt    # Зависимости проекта
├── .env               # Переменные окружения (создайте сами)
└── README.md          # Документация проекта
```

## Логирование

Бот ведёт подробное логирование своей работы. Логи содержат следующую информацию:
- Дата и время события
- Уровень важности
- Описание события

### Уровни логирования:

- **CRITICAL** - Критические ошибки (отсутствие переменных окружения)
- **ERROR** - Ошибки в работе (сбои API, ошибки отправки сообщений)
- **DEBUG** - Служебная информация (успешная отправка сообщений, отсутствие обновлений)

## Примеры логов

```
2021-10-09 15:34:45,150 [ERROR] Сбой в работе программы: Эндпоинт недоступен
2021-10-09 15:34:45,355 [DEBUG] Бот отправил сообщение "Работа взята на проверку"
```

## Обработка ошибок

Бот автоматически обрабатывает следующие ошибки:
- Недоступность API Практикума
- Ошибки в ответе API
- Сбои при отправке сообщений в Telegram
- Отсутствие необходимых переменных окружения

При возникновении ошибок бот:
1. Записывает информацию в лог
2. Отправляет уведомление в Telegram (если это возможно)
3. Продолжает работу после временной ошибки
4. Останавливается при критической ошибке

## Автор

Cоколов Григорий
