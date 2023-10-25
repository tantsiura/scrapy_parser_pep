# Асинхронный парсер на Python (scrapy_parser_pep)

## Описание

Парсер собирает следующую информацию с сайта https://www.python.org/:
- версии языка и авторов версий;
- статусы всех стандартов PEP.

Собранная информация сохраняется в файлы с расширением **csv**:
- Информация о стандарте: номер, статус, автор-(ы);
- Колличество каждого статуса на сайте + общая сумма.

## Технологии
- Python;
- Scrapy.

## Структура парсера

```cmd
scrapy_parser_pep
|   .flake8
|   .gitignore
|   constants.py  <-- Константные данные
|   pytest.ini
|   README.md
|   requirements.txt
|   scrapy.cfg
|
+---pep_parse
|   |   items.py  <-- Создание объекта Items из спарсенных данных
|   |   middlewares.py
|   |   pipelines.py  <-- Обработка Items (запись данных в CSV-файлы)
|   |   settings.py  <-- Настройки парсера
|   |   __init__.py
|   |   
|   +---spiders
|   |   |   pep.py  <-- Метод обработки данных
|   |   |   __init__.py
|   |   |
|   |   \---__pycache__
|   |           
|   \---__pycache__
|           
+---results  <-- Директория с результами парсера
|       pep_2022-08-10T19-36-00.csv  <-- Все полученные данные (номер, статус, автор(ы))
|       status_summary_2022-08-10_22-36-18.csv  <-- Подсчёт кол-ва
|       
+---tests
|
+---venv
```

## Описание работы

Парсер собирает информацию с сайта и сводит все данные в 2 таблицы:
1. Список PEP;
2. Сводка по статусам.
Таблицы находятся в директории **results**.

## Запуск парсера
- Установите вирт. окружение:
    ```python
    python -m venv venv
    ```
- Активируйте вирт. окружение и установите зависимости:
    ```python
    (win) source venv/Scripts/activate
    (linux) source venv/bin/activate
    python -r requirements.txt
    ```
- В терминале введите команду:
    ```python
    scrapy crawl pep
    ```

## Автор

[tantsiura](https://github.com/tantsiura)