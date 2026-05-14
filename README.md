# Парсер данных с сайта hh.ru

Создан новый проект на языке python с применением Flask.
Проект реализован для портфолио сайта [bozheslav.ru](https://bozheslav.com) — [GitHub](https://github.com/Magbusjap/bozheslav).

## 🔗 Live Example

[Смотреть пример на сайте bozheslav.com](https://bozheslav.com/portfolio/pages/parser-dannykh-s-sayta-hhru)

## Стек

![Python](https://img.shields.io/badge/Python-3.12-3776AB?logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-3.x-000000?logo=flask&logoColor=white)
![hh.ru](https://img.shields.io/badge/API-hh.ru-E8001C?logoColor=white)

## Что реализовано

- REST API на Flask с единственным эндпоинтом `GET /search?query=...`
- Запросы к официальному API hh.ru без авторизации
- Возвращает по каждой вакансии: название, компанию, город, опыт, зарплату (от/до/валюта), график, дату публикации, прямую ссылку
- Запуск как системный сервис через systemd
- Интеграция с Laravel-сайтом через `ParserController`

## Стек

- Python 3.12
- Flask
- Requests
- systemd (деплой на Ubuntu 24.04)

## Запуск локально

```bash
git clone https://github.com/Magbusjap/hh-parser-flask
cd hh-parser-flask
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python app.py
```

Проверка:

```bash
curl "http://127.0.0.1:5000/search?query=Laravel"
```

## Пример ответа

```json
{
	"total": 284,
	"shown": 100,
	"vacancies": [
		{
			"name": "PHP-разработчик Laravel",
			"employer": "Компания",
			"city": "Москва",
			"experience": "От 3 до 6 лет",
			"salary_from": 120000,
			"salary_to": 180000,
			"currency": "RUR",
			"schedule": "Полный день",
			"published": "2026-04-01",
			"url": "https://hh.ru/vacancy/..."
		}
	]
}
```

---

<img src="https://bozheslav.com/storage/media/mikgail-bozheslav-favicon-16x16.png" width="16" height="16" alt="bozheslav.com favicon"> [Михаил Божеслав](https://bozheslav.com)
