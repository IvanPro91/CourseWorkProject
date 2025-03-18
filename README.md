# Проект 1. Приложение для анализа банковских операций
```Выбрана категория "Главная страница"```

## О приложении
Приложение реализовано для подчета и вывода аналитических данных с файла excel транзакций, сформированного в банке Тинькофф(Т)

## Данные
Описание данных

* Дата операции — дата, когда произошла транзакция.
* Дата платежа — дата, когда был произведен платеж.
* Номер карты — последние 4 цифры номера карты.
* Статус — статус операции (например, OK, FAILED).
* Сумма операции — сумма транзакции в оригинальной валюте.
* Валюта операции — валюта, в которой была произведена транзакция.
* Сумма платежа — сумма транзакции в валюте счета.
* Валюта платежа — валюта счета.
* Кешбэк — размер полученного кешбэка.
* Категория — категория транзакции.
* MCC — код категории транзакции (соответствует международной классификации).
* Описание — описание транзакции.
* Бонусы (включая кешбэк) — количество полученных бонусов (включая кешбэк).
* Округление на «Инвесткопилку» — сумма, которая была округлена и переведена на «Инвесткопилку».
* Сумма операции с округлением — сумма транзакции, округленная до ближайшего целого числа.

## Описание
Реализован набор функций и главная функция, принимающая на вход строку с датой и временем в формате YYYY-MM-DD HH:MM:SS и возвращающую JSON-ответ со следующими данными:

* Приветствие в формате "???", где ??? — «Доброе утро» / «Добрый день» / «Добрый вечер» / «Доброй ночи» в зависимости от текущего времени.
* По каждой карте:
    * последние 4 цифры карты;
    * общая сумма расходов;
    * кешбэк (1 рубль на каждые 100 рублей).
* Топ-5 транзакций по сумме платежа.
* Курс валют.
* Стоимость акций.

## Реализованные модули
* utils
* views

## Модуль utils
Модуль utils предназначен для реализации функций:

* ```read_finance_excel_operation()``` - Функция для считывания финансовых операций из Excel выдает список словарей с транзакциями.
* ```welcome_text()``` - Функция возврата строки приветствия по дате форматом YYYY-MM-DD HH:MM:SS.
* ```main_cards()``` - Функция вывода всей информации по картам.
* ```top_transactions()``` - Функция возврата ТОП 5 транзакций.
* ```get_api_currency()``` - Функция получения курса валюты по API
* ```get_api_stocks()``` - Функция получения стоимости акций.
* ```currency_rates()``` - Функция возвращает курс валют.
* ```user_stocks()``` - Функция возвращает стоимость акций.
* ```get_user_settings()``` - Функция чтения пользовательских настроек.

## Модуль views
В модуле views реализована главная функция для сбора и отображения данных.

* ```page_main()``` - Функция главной страницы возвращает основную информацию.

## Использование
Необходимо сделать клонирование репозитория по ссылке:
```https://github.com/IvanPro91/CourseWorkProject.git```

Активировать окружение poetry по инструкции на сайте [poetry](https://python-poetry.org/)

Вы можете выгрузить и использовать собственный файл из личного кабинета «Тинькофф Банка» («Т-Банка») или использовать тестовый файл, который уже расположен в директории data.
При условии использования своего файла необходимо его разместить(предварительно переименовав его в operations.xlsx) в директорию data в корне проекта, перед запуском в скрипте main.py задать свое время и дату в нужном формате и запустить.
Вы получите данные в виде JSON:
```commandline
{
  "greeting": "Добрый день",
  "cards": [
    {
      "last_digits": "5814",
      "total_spent": 1262.00,
      "cashback": 12.62
    },
    {
      "last_digits": "7512",
      "total_spent": 7.94,
      "cashback": 0.08
    }
  ],
  "top_transactions": [
    {
      "date": "21.12.2021",
      "amount": 1198.23,
      "category": "Переводы",
      "description": "Перевод Кредитная карта. ТП 10.2 RUR"
    },
    {
      "date": "20.12.2021",
      "amount": 829.00,
      "category": "Супермаркеты",
      "description": "Лента"
    },
    {
      "date": "20.12.2021",
      "amount": 421.00,
      "category": "Различные товары",
      "description": "Ozon.ru"
    },
    {
      "date": "16.12.2021",
      "amount": -14216.42,
      "category": "ЖКХ",
      "description": "ЖКУ Квартира"
    },
    {
      "date": "16.12.2021",
      "amount": 453.00,
      "category": "Бонусы",
      "description": "Кешбэк за обычные покупки"
    }
  ],
  "currency_rates": [
    {
      "currency": "USD",
      "rate": 73.21
    },
    {
      "currency": "EUR",
      "rate": 87.08
    }
  ],
  "stock_prices": [
    {
      "stock": "AAPL",
      "price": 150.12
    },
    {
      "stock": "AMZN",
      "price": 3173.18
    },
    {
      "stock": "GOOGL",
      "price": 2742.39
    },
    {
      "stock": "MSFT",
      "price": 296.71
    },
    {
      "stock": "TSLA",
      "price": 1007.08
    }
  ]
}
```
# Лицензия
MIT