# Цифровой прорыв - Пермь 2023

## **Команда: Зумеры и Бумеры**

Доброе пожаловать в исходный код нашего решения по предсказнию ЧС в Пермском крае. В основе нашей нашей платформы сервис состоящий из Bakcend и Frontend части. Bakcend реализован на Fastapi и его основные команды можно посмотреть и попробовать в специльном списке:
http://45.86.180.208:8000/docs

Frontned написан на Vue.js и также доступ по ссылке:
!ссылка

Сервиз позволяет анализировать вероятности ЧС на ближайщие 10 дней. Основные типы ЧС:

        Взрывы/пожары/разрушения
        Прочие опасности
        Прочие опасности
        Аварии на транспорте
        ЖКХ
        Аварии с выбросом опасных/токсичных веществ
        Опасные природные явлени

Модель машинного обучения анализирует различные показатели и предсказывает вероятностные показатели для каждого из 10 дней. Также предсказание происходит по каждому району отдельно, что позволяет составлять индивидульные потенциальные опасности для каждого из них.

Файлы проекта устроены следующим образом:

---

Backend - папка в внутренней частью сайта
app.py - скрипт содержащий в себе все функции для бэкенда. Запускается через unicorn
static - папка со всеми нужными данными для бэкенда

Отдельно есть Dockerfile. Он позволяет упаковать все в специальный формат. Для этого нужно две команды:

    docker build -t backend_table_getter .
    docker run -p 8000:8000 backend_table_getter

---

ML - папка содержащая все наработки по части модели
Analize.ipynb - содержит в себе анализ данных по обучащей выборке и создание новых признаков(например для ОЯ и НЯ)
Pipeline.ipynb - скрипт, содержащий в себе соединение всех наработанных признаков с созданной разметкой. Далее в нем идет обучение модели, замер качества и сохранение результатов предсказаний за все дни.

---

Frontend

Frontend - папка в внутренней частью сайта
public/data/map - карты проекта
store - для работы с состояниями, запросами
router - переход между страница
components - все компонеты приложения

Отдельно есть Dockerfile. Он позволяет упаковать все в специальный формат. Для этого нужно две команды:

    docker build -t perm .
    docker run -it -p 8080:8080 perm
