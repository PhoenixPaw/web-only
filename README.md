
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
