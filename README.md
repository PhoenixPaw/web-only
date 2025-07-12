<<<<<<< HEAD
# 🚀 PHXPW Staking Bot

Telegram-бот для стейкинга токенов PHXPW на блокчейне TON с поддержкой подключения кошельков, расчета наград в TON/USD и админ-панелью.

## ✨ Возможности

- 🔗 **Подключение кошельков**: Tonkeeper, Telegram Wallet, Seed-фраза
- 💰 **Стейкинг**: Периоды 14, 30, 60, 90, 180 дней
- 📊 **Расчет доходов**: В TON с актуальным курсом к USD
- 💱 **Актуальные курсы**: TON/USD и PHXPW/TON с обновлением каждые 5 минут
- 📢 **Рекламные вставки**: Автоматическое отображение рекламы в интерфейсе
- ⚙️ **Админ-панель**: Управление периодами, выплаты, статистика
- 🔄 **Автоматизация**: Ежедневные награды, планировщик задач
- 🛡️ **Безопасность**: Валидация адресов, безопасное хранение данных

## 🛠️ Установка

### 1. Клонирование репозитория
```bash
git clone <repository-url>
cd staking
```

### 2. Установка зависимостей
```bash
pip install -r requirements.txt
```

### 3. Настройка переменных окружения
Создайте файл `.env` в корневой директории:

```env
# Telegram Bot
TELEGRAM_BOT_TOKEN=your_bot_token_here
ADMIN_USER_ID=your_admin_telegram_id

# База данных Supabase
DB_HOST=your_supabase_host
DB_PORT=5432
DB_NAME=postgres
DB_USER=postgres
DB_PASSWORD=your_supabase_password

# TON API
TON_API_KEY=your_ton_api_key
TON_TOKEN_ADDRESS=your_phxpw_token_address
REWARD_WALLET_ADDRESS=your_reward_wallet_address
TON_REWARD_WALLET_SEED=your_reward_wallet_seed_phrase
```

### 4. Запуск бота
```bash
python main.py
```

## 📋 Структура проекта

```
staking/
├── main.py                 # Главный файл бота
├── handlers/               # Обработчики команд
│   ├── user_handlers.py    # Пользовательские команды
│   ├── admin_handlers.py   # Админ-команды
│   └── staking_handlers.py # Команды стейкинга
├── services/               # Бизнес-логика
│   ├── staking_service.py  # Сервис стейкинга
│   └── ton_service.py      # TON API интеграция
├── database/               # База данных
│   ├── database.py         # Менеджер БД
│   └── models.py           # Модели данных
├── scheduler.py            # Планировщик задач
├── tests/                  # Тесты
└── requirements.txt        # Зависимости
```

## 🔧 Конфигурация

### Переменные окружения

| Переменная | Описание | Обязательная |
|------------|----------|--------------|
| `TELEGRAM_BOT_TOKEN` | Токен Telegram бота | ✅ |
| `ADMIN_USER_ID` | ID администратора в Telegram | ✅ |
| `DB_HOST` | Хост базы данных Supabase | ✅ |
| `DB_PASSWORD` | Пароль базы данных | ✅ |
| `TON_API_KEY` | Ключ TON API | ✅ |
| `TON_TOKEN_ADDRESS` | Адрес токена PHXPW | ✅ |
| `REWARD_WALLET_ADDRESS` | Адрес reward кошелька | ✅ |
| `TON_REWARD_WALLET_SEED` | Seed-фраза reward кошелька | ✅ |

### Настройка периодов стейкинга

Периоды стейкинга настраиваются через админ-панель:
- Название периода
- Дата начала и окончания
- Коэффициент награды (APY)

### Настройка цен и рекламы

**Автоматическое обновление цен:**
- Курс TON к USD обновляется каждые 5 минут
- Цена PHXPW к TON обновляется каждые 5 минут
- Кеширование для снижения нагрузки на API

**Рекламные вставки:**
- Отображаются во всех основных разделах бота
- Настраиваются в коде сервиса TON
- Автоматическое форматирование с курсами валют

## 🚀 Запуск в продакшене

### 1. Подготовка сервера
```bash
# Обновление системы
sudo apt update && sudo apt upgrade -y

# Установка Python
sudo apt install python3 python3-pip python3-venv -y

# Создание виртуального окружения
python3 -m venv venv
source venv/bin/activate
```

### 2. Установка зависимостей
```bash
pip install -r requirements.txt
```

### 3. Настройка systemd сервиса
Создайте файл `/etc/systemd/system/phxpw-staking-bot.service`:

```ini
[Unit]
Description=PHXPW Staking Bot
After=network.target

[Service]
Type=simple
User=your_user
WorkingDirectory=/path/to/staking
Environment=PATH=/path/to/staking/venv/bin
ExecStart=/path/to/staking/venv/bin/python main.py
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```

### 4. Запуск сервиса
```bash
sudo systemctl daemon-reload
sudo systemctl enable phxpw-staking-bot
sudo systemctl start phxpw-staking-bot
```

### 5. Проверка статуса
```bash
sudo systemctl status phxpw-staking-bot
sudo journalctl -u phxpw-staking-bot -f
```

## 🧪 Тестирование

### Запуск тестов
```bash
# Модульные тесты
python -m pytest tests/unit/

# Интеграционные тесты
python -m pytest tests/integration/

# Все тесты
python -m pytest tests/
```

### Тестирование бота
```bash
# Тест инициализации
python test_bot_simple.py

# Тест валидации адресов
python test_wallet_validation.py

# Тест подключения к БД
python test_db_connection.py

# Тест отображения цен и рекламы
python test_simple_price.py

# Полный тест цен с API
python test_price_display.py
```

## 📊 Мониторинг

### Логи
Логи сохраняются в системном журнале:
```bash
sudo journalctl -u phxpw-staking-bot -f
```

### Метрики
- Количество активных пользователей
- Общая сумма в стейкинге
- Выплаченные награды
- Статус подключения к API

## 🔒 Безопасность

### Рекомендации
- Используйте HTTPS для всех API запросов
- Храните seed-фразы в зашифрованном виде
- Регулярно обновляйте зависимости
- Мониторьте логи на подозрительную активность
- Используйте firewall для ограничения доступа

### Валидация
- Проверка формата адресов кошельков
- Валидация seed-фраз
- Проверка балансов через API
- Защита от SQL-инъекций

## 🆘 Устранение неполадок

### Частые проблемы

1. **Ошибка подключения к БД**
   ```bash
   # Проверьте переменные окружения
   echo $DB_HOST $DB_PASSWORD
   
   # Проверьте подключение
   python test_db_connection.py
   ```

2. **Ошибка TON API**
   ```bash
   # Проверьте API ключ
   curl "https://toncenter.com/api/v2/getAddressBalance?address=EQ...&api_key=YOUR_KEY"
   ```

3. **Бот не отвечает**
   ```bash
   # Проверьте статус сервиса
   sudo systemctl status phxpw-staking-bot
   
   # Проверьте логи
   sudo journalctl -u phxpw-staking-bot -n 50
   ```

### Восстановление после сбоя
```bash
# Перезапуск сервиса
sudo systemctl restart phxpw-staking-bot

# Проверка состояния БД
python -c "from database.database import db_manager; print(db_manager.health_check())"
```

## 📈 Развитие проекта

### Планируемые функции
- [ ] Интеграция с DEX для автоматического свапа
- [ ] Мобильное приложение
- [ ] Веб-интерфейс для админов
- [ ] Аналитика и графики
- [ ] Уведомления о важных событиях

### Вклад в проект
1. Форкните репозиторий
2. Создайте ветку для новой функции
3. Внесите изменения
4. Создайте Pull Request

## 📞 Поддержка

- **Telegram**: @PhoenixPawcreator
- **Email**: support@phoenixpaw.com
- **Документация**: [Wiki проекта]

## 📄 Лицензия

MIT License - см. файл [LICENSE](LICENSE) для подробностей.

---

**Версия**: 1.0.0  
**Последнее обновление**: 21.06.2025  
**Автор**: PhoenixPaw Team 
=======
# PHXPW Staking Web

Веб-интерфейс для интеграции с Tonkeeper для PHXPW Staking Bot.

## Структура файлов

```
phxpw-staking-web/
├── index.html              # Главная страница подключения кошелька
├── tonconnect-manifest.json # Manifest для Tonkeeper
├── terms.html              # Условия использования
├── privacy.html            # Политика конфиденциальности
└── README.md               # Этот файл
```

## Настройка GitHub Pages

1. Создайте репозиторий `phxpw-staking-web` на GitHub
2. Загрузите все файлы в корень репозитория
3. Включите GitHub Pages:
   - Settings → Pages
   - Source: Deploy from a branch
   - Branch: main
   - Folder: / (root)

## URL после настройки

После включения GitHub Pages ваш сайт будет доступен по адресу:
```
https://YOUR_USERNAME.github.io/phxpw-staking-web/
```

## Обновление в боте

В файле `handlers/user_handlers.py` обновите URL:
```python
tonkeeper_url = "https://app.tonkeeper.com/connect/dapp?manifestUrl=https://YOUR_USERNAME.github.io/phxpw-staking-web/tonconnect-manifest.json"
```

## Проверка

После настройки проверьте:
1. https://YOUR_USERNAME.github.io/phxpw-staking-web/tonconnect-manifest.json
2. https://YOUR_USERNAME.github.io/phxpw-staking-web/
3. https://YOUR_USERNAME.github.io/phxpw-staking-web/terms.html
4. https://YOUR_USERNAME.github.io/phxpw-staking-web/privacy.html

## Функции

- **index.html**: Страница подключения кошелька Tonkeeper
- **tonconnect-manifest.json**: Описание приложения для Tonkeeper
- **terms.html**: Условия использования сервиса
- **privacy.html**: Политика конфиденциальности

## Безопасность

- Seed-фразы не сохраняются
- Все данные шифруются
- HTTPS обязателен для работы с Tonkeeper 
>>>>>>> 692320918ad57371b0cf2757b20b49d42d53a412
