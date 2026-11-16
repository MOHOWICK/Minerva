# Minerva 🦉
[![Version](https://img.shields.io/github/v/release/MOKHOVIK/minerva?include_prereleases&label=version&color=blue)](https://github.com/MOKHOVIK/minerva/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/python-3.13-blue.svg)](https://www.python.org/downloads/)
[![Django](https://img.shields.io/badge/django-5.0-green.svg)](https://www.djangoproject.com/)

**Minerva** — это локальная галерея для сгенерированных артов (*ComfyUI / Stable Diffusion*). Умное хранение оригиналов и превью, удобный поиск по промптам, фильтры по моделям и встроенная база знаний с заметками. Ваш приватный архив работ с красивым интерфейсом.

---
## ✨ Основные возможности
* **Умная загрузка**: Загрузка пачками с автоматическим парсингом метаданных (*промпты, сид, модель, шаги*) прямо из PNG-файлов ComfyUI.
* **Оптимизация хранилища**: Конвертация в JPG для оригиналов и WebP для превью, шардирование файлов по папкам (*ULID*) для быстрой работы с тысячами артов.
* **Галерея**: Адаптивная сетка (*Masonry*), ленивая загрузка, фильтрация по моделям и категориям, поиск по Positive и Negative промптам.
* **Статистика**: Интерактивные графики (*Chart.js*) по активности, топ-моделям, разрешениям и самым частым тегам с возможностью настройки игнорируемых слов.
* **База знаний**: Заметки с категориями и markdown-поддержкой для хранения удачных комбинаций тегов и лайфхаков.
* **Админка**: Удобное управление артами, пользователями и настройками.
* **Безопасность**: Полная изоляция данных пользователей, кастомные страницы ошибок.

## 🛠️ Технологии
* **Backend**: Python 3.13, Django 5.0
* **Frontend**: Bootstrap 5.3, Chart.js, FontAwesome, Masonry.js
* **База данных**: SQLite (*с включенным WAL-режимом*)
* **Обработка изображений**: Pillow
* **Инфраструктура**: Docker, Docker Compose, Nginx, Gunicorn

<details>
<summary><b>🐳 Запуск через Docker</b></summary>

1. Клонируйте репозиторий:
    ```bash
    git clone https://github.com/MOKHOVIK/Minerva.git
    cd minerva
2. Создайте файл .env на основе .env.example и заполните свои данные:
    ```bash
    cp .env.example .env
3. Запустите контейнеры
    ```bash
    docker-compose up -d --build
4. Создайте суперпользователя (главного админа):
    ```bash
    docker-compose exec web python manage.py createsuperuser
5. [Откройте сайт](http://localhost)
</details>

<details>
<summary><b>💻 Локальная разработка (без Docker)</b></summary>

1. Клонируйте репозиторий:
    ```bash
    git clone https://github.com/MOKHOVIK/Minerva.git
    cd minerva
    ```
2. Создайте виртуальное окружение и установите зависимости:
    ```bash
    # Windows
    python -m venv .venv
    .venv\Scripts\activate

    # Linux / macOS
    python3 -m venv .venv
    source .venv/bin/activate
3. Примените миграции:
    ```bash
    python manage.py migrate
4. Создайте админа:
    ```bash
    python manage.py migrate
5. Создайте файл .env на основе .env.example и заполните свои данные:
    ```bash
    cp .env.example .env
6. Запустите сервер:
    ```bash
    python manage.py runserver
    ```
</details>

<details>
<summary><b>🔄 Обновление проекта</b></summary>

Если вы уже склонировали проект и хотите обновиться до последней версии, выполните следующие шаги.
### Обновление через Docker
1.  Перейдите в папку с проектом и скачайте изменения:
    ```bash
    git pull origin main
2. Если изменился requirements.txt (добавились новые библиотеки), пересоберите контейнеры:
    ```bash
    docker-compose up -d --build
    ```
    (Если зависимости не менялись, можно просто выполнить `docker-compose restart`)
3. Примените новые миграции (если в новой версии менялась структура базы):
    ```bash
    docker-compose exec web python manage.py migrate
### Обновление при локальной разработке (без Docker)
1. Активируйте виртуальное окружение:
    ```bash
    # Windows
    .venv\Scripts\activate

    # Linux / macOS
    source .venv/bin/activate
2. Скачайте изменения из репозитория:
    ```bash
    git pull origin main
3. Обновите зависимости (*на случай, если они изменились*):
    ```bash
    pip install -r requirements.txt
4. Примените миграции:
    ```bash
    python manage.py migrate
5. Перезапустите сервер:
    ```bash
    python manage.py runserver
    ```
</details>

## 📁 Структура проекта
```
Minerva/
├── apps/
│   ├── core/       # Ядро (главная, авторизация, настройки)
│   ├── artworks/   # Всё про арты (модели, загрузка, галерея)
│   └── notes/      # База знаний (заметки, категории)
├── config/         # Настройки Django
├── nginx/          # Конфигурация Nginx
├── static/         # CSS, JS, шрифты, картинки интерфейса
├── templates/      # HTML-шаблоны
├── .data/          # Хранилище (БД и арты, в git не попадает)
├── docker-compose.yml
├── Dockerfile
└── manage.py
```

## 📄 Лицензия
Этот проект распространяется под лицензией MIT. Подробности в файле [LICENSE](https://github.com/MOKHOVIK/Minerva/blob/main/LICENSE).