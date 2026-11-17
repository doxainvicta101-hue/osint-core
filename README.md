# osint-core
My pet project for automation and data collection
🇷🇺
# OSINT Bot 3.0

Telegram-бот для поиска открытой информации по телефону, почте, нику, ссылке, ИНН, IP, домену, криптокошельку и другим данным. Работает только с открытыми источниками.

## Возможности

- Телефон: оператор, регион, часовой пояс, проверка через внешние сервисы.
- Почта: проверка регистраций в открытых сервисах, утечки (только названия баз).
- Никнейм и username: поиск профилей в соцсетях и на платформах.
- Соцсети и Telegram: публичные данные профилей.
- Персона и ФИО: поиск по открытым источникам, шаблоны дорков.
- Бизнес: ИНН, карточки юрлиц и ИП.
- Сеть: IP, WHOIS, DNS, проверка сайта, раскрытие коротких ссылок.
- Крипто: последняя активность адресов ETH и TRON, TON.
- Медиа и геолокация: EXIF фото, метаданные документов (pdf, docx, xlsx), /geo, /revgeo, /img.
- /case: сводный отчёт по нескольким данным с извлечением сущностей.
- Отчёты в HTML по кнопке.
- Админ-панель: /diag, /defupdate, журнал запросов.

## Требования

- Python 3.9 и новее.
- Linux (VPS, Debian/Ubuntu) или Android с Termux.
- Токен бота от [@BotFather](https://t.me/BotFather).
- Свой Telegram ID (узнать можно у [@userinfobot](https://t.me/userinfobot)).

## Установка и запуск

1. Распакуйте архив в отдельную папку.
2. Запустите установку:

```
bash install.sh
```

Скрипт установит Python и зависимости, создаст `.env` из шаблона и остановится. Заполните `.env`:

```
BOT_TOKEN=токен_от_BotFather
ADMIN_ID=ваш_telegram_id
```

3. Запустите скрипт ещё раз. Он стартует бота:

```
bash install.sh
```

Дальнейший запуск без переустановки: `.venv/bin/python bot.py` из папки проекта.

На Android удобнее не закрывать Termux и не давать ему уходить в сон (`termux-wake-lock`).

## Настройка .env

Полный список переменных с пояснениями находится в `.env.example`. Обязательны только `BOT_TOKEN` и `ADMIN_ID`. Остальные ключи API необязательны: без них соответствующие проверки просто не работают.

- `GITHUB_TOKEN` поднимает лимит GitHub API с 60 до 5000 запросов в час.
- `IPAPI_KEY` нужен для коммерческого использования ip-api.com. Бесплатный тариф ip-api.com разрешён только для некоммерческого использования.
- `BREACH_CHECK=0` отключает проверку почты по базам утечек. Пока проверка включена, адрес почты передаётся сервису XposedOrNot.
- `TG_PROXY` и `WEB_PROXY` задают прокси для Telegram и веб-запросов.

Необязательные внешние утилиты `holehe` и `ignorant` ставятся отдельно (`pip install holehe ignorant`). Если их версия выводит другие аргументы, поправьте `HOLEHE_CMD` и `IGNORANT_CMD`.

## Команды

Список команд доступен в боте по `/start`. Для администратора дополнительно доступны `/id`, `/idstat`, `/diag`, `/defupdate`.

## Данные

Всё, что бот сохраняет (журнал, отчёты, списки доступа), лежит в папке `data/` внутри проекта или в каталоге, указанном в `DATA_DIR`. Не передавайте эту папку третьим лицам.

## Важно

Использование бота регулируется [условиями использования](TERMS.md). Перед запуском прочитайте их.

🇬🇧

OSINT Bot 3.0

A Telegram bot for searching open-source information by phone number, email, username, link, TIN (INN), IP address, domain, crypto wallet, and other data. It works strictly with open sources.

Features

• Phone: Carrier, region, time zone, verification via external services.
• Email: Checking registrations on public services, data breaches (database names only).
• Nickname and username: Searching for profiles across social networks and platforms.
• Social networks and Telegram: Public profile data.
• Person and full name: Search across open sources, dork templates.
• Business: TIN (INN), legal entity and sole proprietor profiles.
• Network: IP, WHOIS, DNS, website check, expanding short links.
• Crypto: Recent activity for ETH, TRON, and TON addresses.
• Media and geolocation: Photo EXIF, document metadata (pdf, docx, xlsx), /geo, /revgeo, /img.
• /case: Consolidated report across multiple inputs with entity extraction.
• Reports: Exportable HTML reports at the click of a button.
• Admin panel: /diag, /defupdate, request log.

Requirements

• Python 3.9 or higher.
• Linux (VPS, Debian/Ubuntu) or Android with Termux.
• Bot token from @BotFather.
• Your Telegram ID (you can get it from @userinfobot).

Installation and Launch

1. Extract the archive into a separate folder.
2. Run the installation script:
bash
bash install.sh

The script will install Python and dependencies, create a .env file from the template, and pause. Fill in the .env file:
env
BOT_TOKEN=token_from_BotFather
ADMIN_ID=your_telegram_id

3. Run the script again to start the bot:
bash
bash install.sh

For subsequent launches without reinstalling, run .venv/bin/python bot.py from the project folder.
On Android, it is best to keep Termux open and prevent it from sleeping (termux-wake-lock).

Configuring .env

A full list of variables with explanations can be found in .env.example. Only BOT_TOKEN and ADMIN_ID are required. Other API keys are optional—without them, the corresponding checks will simply be skipped.
• GITHUB_TOKEN increases the GitHub API rate limit from 60 to 5,000 requests per hour.
• IPAPI_KEY is required for commercial use of ip-api.com. The free tier of ip-api.com is permitted for non-commercial use only.
• BREACH_CHECK=0 disables checking emails against breach databases. While enabled, the email address is sent to the XposedOrNot service.
• TG_PROXY and WEB_PROXY configure proxies for Telegram and web requests.
Optional external utilities holehe and ignorant are installed separately (pip install holehe ignorant). If your installed version uses different CLI arguments, adjust HOLEHE_CMD and IGNORANT_CMD accordingly.

Commands

The list of commands is available inside the bot via /start. Administrators additionally have access to /id, /idstat, /diag, and /defupdate.

Data

Everything the bot saves (logs, reports, access lists) is stored in the data/ folder inside the project directory or in the path specified by DATA_DIR. Do not share this folder with third parties.

Important

Use of this bot is governed by the Terms of Use. Please read them before running the bot