# Рассчет средней заработной платы программиста

Проект представляет собой скрипт, собирающий информацию о зарплате программистов в Москве за последний месяц.

Для каждого языка программирования статистика рассчитывается отдельно. Для подсчета статистики взят топ 12 (из 15) самых популярных языков
программирования [по версии Github](https://habr.com/ru/post/310262/).
Источниками информации для сбора данных являются [HeadHunter](https://www.hh.ru) и [SuperJob](https://www.superjob.ru).

Т.к. многие вакансии опубликованы без указания з/п или в других валютах, то при подсчете статистики, для соблюдения точности,
соблюдались определенные нюансы:

 - Зарплата указана в рублях
 - Указан минимальный или максимальный уровень з/п
 - В случае с HeadHunter, если вакансий для языка найдено меньше 100, то данный язык в подсчете не участвует

### Как установить

Для корректной работы вам понадобится указать в файле ```.env```:

- SECRET_KEY (API-токен сайта SuperJob), его можно получить после регистрации вашего приложения на их официальном сайте API [SuperJob](https://api.superjob.ru)

В итоге эти данные должны быть внесены в ```.env``` файл в таком виде:
```
SECRET_KEY=N=API-токен сайта SuperJob
```

Python3 должен быть уже установлен. 
Затем используйте `pip` (или `pip3`, есть конфликт с Python2) для установки зависимостей:
```
pip install -r requirements.txt
```
### Запуск
Для вывода таблицы со статистикой за последние 30 дней, введите в консоли:

```commandline
python main.py
```

 Пример работы программы:
```commandline
┌ HeadHunter Moscow ────┬──────────────────┬─────────────────────┬──────────────────┐
│ Язык программирования │ Вакансий найдено │ Вакансий обработано │ Средняя зарплата │
├───────────────────────┼──────────────────┼─────────────────────┼──────────────────┤
│ JavaScript            │ 860              │ 765                 │ 207628           │
│ Java                  │ 313              │ 264                 │ 265185           │
│ Python                │ 466              │ 404                 │ 230230           │
│ C++                   │ 362              │ 330                 │ 201572           │
│ C#                    │ 268              │ 235                 │ 213466           │
│ C                     │ 948              │ 894                 │ 201866           │
│ Go                    │ 166              │ 140                 │ 287611           │
│ TypeScript            │ 264              │ 215                 │ 238150           │
└───────────────────────┴──────────────────┴─────────────────────┴──────────────────┘

┌ SuperJob Moscow ──────┬──────────────────┬─────────────────────┬──────────────────┐
│ Язык программирования │ Вакансий найдено │ Вакансий обработано │ Средняя зарплата │
├───────────────────────┼──────────────────┼─────────────────────┼──────────────────┤
│ JavaScript            │ 41               │ 31                  │ 97679            │
│ Java                  │ 17               │ 5                   │ 186000           │
│ Python                │ 36               │ 23                  │ 117699           │
│ Ruby                  │ 3                │ 1                   │ 450000           │
│ C++                   │ 12               │ 4                   │ 158250           │
│ C#                    │ 4                │ 4                   │ 255000           │
│ C                     │ 12               │ 3                   │ 141666           │
│ Go                    │ 5                │ 1                   │ 425000           │
│ Objective-C           │ 2                │ 0                   │ 0                │
│ Scala                 │ 1                │ 1                   │ 240000           │
│ Swift                 │ 3                │ 1                   │ 420000           │
│ TypeScript            │ 8                │ 2                   │ 78000            │
└───────────────────────┴──────────────────┴─────────────────────┴──────────────────┘
```

### Цель проекта

Код написан в образовательных целях на онлайн-курсе для веб-разработчиков [dvmn.org](https://dvmn.org/).