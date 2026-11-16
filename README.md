# Minerva 🦉
[![Version](https://img.shields.io/github/v/release/MOKHOVIK/minerva?include_prereleases&label=version&color=blue)](https://github.com/MOKHOVIK/minerva/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/python-3.13-blue.svg)](https://www.python.org/downloads/)
[![Django](https://img.shields.io/badge/django-5.0-green.svg)](https://www.djangoproject.com/)

> 📚 **Вся подробная документация (установка, настройка, обновление) находится в [Wiki проекта]([https://github.com/ваш_ник/minerva/wiki](https://github.com/MOKHOVIK/Minerva/wiki)).**
> Здесь вы найдете ответы на все вопросы.

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
