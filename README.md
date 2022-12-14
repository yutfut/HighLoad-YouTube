# HighLoad-YouTube
Технопарк Mail.ru 3 семестр.

## Содержание

* ### [1. Тема и целевая аудитория](#1)
* ### [2. Расчет нагрузки](#2)
* ### [3. Логическая схема](#3)
* ### [4. Физическая схема](#4)
* ### [5. Технологии](#5)
* ### [6. Схема проекта](#6)
* ### [7. Список серверов](#7)
* ### [8. Источники](#8)

## 1. Тема и целевая аудитория <a name="1"></a>
**YouTube**  — видеохостинг, предоставляющий пользователям услуги хранения, доставки и показа видео.

### MVP
- Регистрация 
- Загрузка видео
- Просмотр видео
- Комментирование видео
- Лайк

### Целевая аудитория
У [**YouTube**](https://www.globalmediainsight.com/blog/youtube-users-statistics/) более 2,6 миллиардов активных пользователей в месяц.

| **Страна**              | **Количество пользователей в месяц, млн** |
| ----------------------- | ----------------------------------------- |
| India                   | 467                                       |
| USA                     | 240                                       |
| Indonesia               | 127                                       |
| Brazil                  | 107                                       |
| Russia                  | 99                                        |
| Japan                   | 93.8                                      |
| Mexico                  | 74.1                                      |
| Germany                 | 66                                        |
| Pakistan                | 55.7                                      |
| Vietnam                 | 54.2                                      |

## 2. Расчет нагрузки <a name="2"></a>
### Продуктовые метрики
* Месячная аудитория - 2.6 млрд
* Дневная аудитория - 122 млн
* Средний размер хранилища пользователя - 2 Мб (аватарка и данные о пользователе)
* Среднее количество действий пользователя по типам в день
  >[Средний пользователь тратит 23,2 часа в месяц на просмотр контента.](https://lpgenerator.ru/blog/2021/10/07/statistika-youtube-kotoruyu-nuzhno-znat-v-2021/#obshchaya-statistika-youtube-2021)
 
  23.2 * 60 / 30 = 46.4 минут просмотра в день.
  >[Cредняя длительность видео на YouTube 8.4 минуты](https://exlibris.ru/news/statistika-youtube-2019-infografika/#:~:text=%D0%9F%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D1%82%D0%B5%D0%BB%D0%B8%20%D1%81%D0%BC%D0%BE%D1%82%D1%80%D1%8F%D1%82%20%D0%B2%D0%B8%D0%B4%D0%B5%D0%BE%20%D0%BA%D0%B0%D0%B6%D0%B4%D1%8B%D0%B9%20%D0%B4%D0%B5%D0%BD%D1%8C&text=%D0%92%20%D1%81%D1%80%D0%B5%D0%B4%D0%BD%D0%B5%D0%BC%20%D0%BD%D0%B0%20%D0%BA%D0%B0%D0%B6%D0%B4%D0%BE%D0%B3%D0%BE%20%D1%87%D0%B5%D0%BB%D0%BE%D0%B2%D0%B5%D0%BA%D0%B0,%D0%BF%D0%BE%D1%8D%D1%82%D0%BE%D0%BC%D1%83%20%D1%81%D1%80%D0%B5%D0%B4%D0%BD%D0%B8%D0%B5%20%D0%BF%D0%BE%D0%BA%D0%B0%D0%B7%D0%B0%D1%82%D0%B5%D0%BB%D0%B8%20%D1%82%D0%B0%D0%BA%D0%B8%D0%B5%20%D0%B2%D0%BF%D0%B5%D1%87%D0%B0%D1%82%D0%BB%D1%8F%D1%8E%D1%89%D0%B8%D0%B5.)
  
  46.4 / 8.4 = 5.5 видео просматривает один пользаватель за сутки.
  >[пользователи в стреднем ставят](https://tubularlabs.com/blog/3-metrics-youtube-success/) 4 лайка на 100 видео
  
  получаем что в среднем пользователь смотрит 5.5 видео в день и около 165 в месяц, отсюда делаем вывод что пользователь ставит в месяц 6 лайков

  > [пользователи в среднем оставляю](https://tubularlabs.com/blog/3-metrics-youtube-success/) 5 комментариев на 1000 видео
  
  получаем что в среднем пользователь оставляет 1 комментарий в месяц.

  | **Действие**           | **Среднее количество в месяц** |
  | -----------------------| -------------------------------|
  | Лайк                   | 6                              |
  | Комментарий            | 1                              |

### Технические метрики
#### Размер хранения
* #### Видео
> Каждую минуту на YouTube загружается более  500 часов нового контента.\
> [1 час видео весит 8 Гб.](http://7youtube.ru/news/skolko-vesit-video.html)

За сутки получаем 
> 24 * 500 * 8 = 96 000Гб

За год
> 96 000 * 365 = 34 218 Пб

За пять лет
> 34 218 * 5 = 171 093 Пб

Так как все видео надо хранить минимум в двух экземплярах

> 342 186 Пб

#### Сетевой трафик
> В среднем посетитель просматривает 46.4 минуты контента в сутки.
* #### Просмотр ежедневно
> 46.4 * 60 = 2784 секунд.

> 122 млн * 2784 = 339 648 млн секунд = 94.34 млн часов просматривается в течении суток.

[1 час видео весит 8 Гб](http://7youtube.ru/news/skolko-vesit-video.html)

> 94.34 млн часов * 8 Гб = 754,72 млн Гб за сутки

> 754,72 млн Гб /  (24 * 60 * 60) = 754,72 / 86 400 = 8 735 млн Гб в секунду

* #### Загрузка видео

> 24 * 60 * 500 = 720 000 часов видео загружается ежедневно

> 720 000 * 8 = 5.76 млн Гб видео загружается ежедненво

> 5.76 / 86 400 = 66.6 тыс Гб в секуну 

#### RPS в разбивке по типам запросов
Пользователи выбирают видео для просмотра тремя способами
1. С главной страницы: home page -> video
2. Через рекомендации: home page -> recommendation -> video
3. Через поиск:        home page -> search -> video

Для загрузки главной страницы совершается 79 запросов.\
4 запроса к API.\
75 запросов к статике.

Для загрузки страницы поиска совершается 60 запросов.\
4 запроса к API.\
56 запросов к статике.

Для загрузки страницы рекомендаций совершается 63 запросов.\
4 запроса к API.\
59 запросов к статике.

Для загрузки страницы видо совершается 62 запросов.\
4 запроса к API.\
58 запросов к статике.

Предположим пользователь каждым способ смотрит по два видео:
1. С главной страницы
####Всего запросов
> 79 + 62 = 141 Для просмотра одного видео с главной страницы.
 
> 141 * 2 = 282

> 282 * 122 млн = 34 404 млн запросов.

####Запросы на бэк
> 4 + 4 = 8 Запросов на бэк для просмотра одного видео с главной страницы.

> 8 * 2 = 16

> 16 * 122 млн = 1 952 млн запросов на бэк.

2. Через рекомендации
####Всего запросов
>79 + 63 + 62 = 204 Для просмотра одного видео через рекомендации.

> 204 * 2 = 408

> 408 * 122 млн = 49 776 млн запросов.
####Запросы на бэк
> 4 + 4 + 4 = 12 Запросов на бэк для просмотра одного видео с главной страницы.

> 12 * 2 = 24

> 24 * 122 млн = 2 928 млн запросов на бэк.
3. Через поиск
####Всего запросов
>79 + 60 + 62 = 201 Для просмотра одного видео через рекомендации.

> 201 * 2 = 402

> 402 * 122 млн = 49 044 млн запросов.
####Запросы на бэк
> 4 + 4 + 4 = 12 Запросов на бэк для просмотра одного видео с главной страницы.

> 12 * 2 = 24

> 24 * 122 млн = 2 928 млн запросов на бэк.

###Запрросы на Nginx
> 34 404 + 49 776 + 49 044 = 133 224 млн запросов в сутки

> 133 224 млн / (24 * 60 * 60) = 1 541 944 RPS

### Запросы на бэк 
> 1 952 + 2 928 + 2 928 = 7808 млн запросов в сутки

> 7808 млн / (24 * 60 * 60) = 90 370 RPS

[пользователи в стреднем ставят](https://tubularlabs.com/blog/3-metrics-youtube-success/) 4 лайка на 100 видео
>  122 млн * 5.5 = 671 млн видео просматривается за сутки\
>  671 млн * 4% = 26.84 млн лайков за сутки\
>  26.84 млн / (24 * 60 * 60) = 310 rps

[пользователи в среднем оставляю](https://tubularlabs.com/blog/3-metrics-youtube-success/) 5 комментариев на 1000 видео
> 122 млн * 5.5 = 671 млн видео просматривается за сутки\
> 671 млн * 0.5% = 3.355 млн коментариев за сутки\
> 3.355 млн / (24 * 60 * 60) = 38 rps

Чтобы загрузить видео необходимо сделать 4 запроса.\
Каждую минуту на YouTube загружается более  500 часов нового контента.\
Средняя длительность видео 8.4 минуты.

> 500 * 60 / 8.4 = 3571 видео в минуту ставится на загрузку\
> 3571 * 60 * 24 = 5142240 видео за сутки ставится на загрузку\
> 5.14 млн * 4 запроса = 20.56 млн запрос в сутки\
> 20.56 млн / (24 * 60 * 60) = 237 rps

Сумарный RPS на бэк

> 90 370 + 310 + 38 + 237 = 90 955 RPS

| **Действие**           | **RPS**   |
| -----------------------| ----------|
| Nginx                  | 1 541 944 |
| Back                   | 90 955    |

## 3. Логическая схема <a name="3"></a>
![](https://github.com/yutfut/HighLoad-YouTube/blob/master/image/db.jpg)

## 4. Физическая схема <a name="4"></a>
* ### Хранение сессий пользователей
Для хранения сессий будем использовать in-memory Redis. Благодаря тому, что Redis является in-memory базой данных, то доступ к определенной записи будет практически равен доступу к оперативной памяти. Помимо свой быстроты Redis поддерживает неблокирующую master-slave репликацию из коробки.
* ### Хранение видео
По типу хранения видео можно разделить на категории:
1. HDD
2. SSD

Изначально все видео будут загружаться на HDD, но те видео которые будут иметь популярность, будем копировать на SSD, чтобы отдавать быстрее, когда популярность будет проходить они будут удаляться с SSD.
* ### Профили, лайки, комментарии
Данные, для которых необходима надежность и не нужен столь быстрый доступ(профили, комментарии, лайки) будем хранить в Postgresql. Для повышения доступности и надеждности сервиса будем использовать технологию шардирования и в разных шардах будем хранить информацию о разных сущностях проекта.

## 5. Технологии <a name="5"></a>
|технология    |область примерения|мотивационная часть|
|--------------|------------------|-------------------|
|js, html, css|Frontend|набор технологий наиболее популярный на рынке, поэтому для него всегда можно найти разработчиков.                   |
|React|Библиотека Frontend|Ускорит процесс разработки.|
|Go|Backend|Быстрый, компилируемый, обладает удобный параллелизм, а также он прост в освоении командой разработки.|
|GRPC|Backend||
|C/C++|Backend|Обеспечить максимальную скорость в самых нагруженных частях проекта.|
|Redis|Хранение сессий|In-memory БД позволяет обеспечить высокую скорость на чтение и запись.|
|Postgresql|Хранение пользователей, комментариев, лайков|Обладает хорошей функциональностью и поддержкой.|
|Nginx|Web-server Reverse proxy|Быстрый, прост в найстройке и использовании.|
|GitLab CI|Система контроля версий.|Линтеры, юнит-тесты, end to end тесты, selenium|
|Kubernetes|Deploy||
## 6. Схема проекта <a name="6"></a>

![](https://github.com/yutfut/HighLoad-YouTube/blob/master/image/HL_2.jpg)

## 7. Список серверов <a name="7"></a>
Для расположения такого колличества серверов можно воспользоваться услугами компании [Amazon](https://aws.amazon.com/ru/about-aws/global-infrastructure/regional-product-services/?p=ngi&loc=4), чьи дата-центры находятся по всему миру. Можно равномерно расположить сервера по ДЦ для увелечения стабильности. \
Важно расположить сервера в центральной Азии из-за большой плотности насления и большого кол-ва бедных стран, что является причной преимущественно слабых и мобильных устройств, а так же плохой связи 
* Северная Америка (Калифорния)
* Бразилия (Сан-Паулу)
* Европа (Франкфурт)
* Индия (Мумбаи)
* Китай (Гонконг)
* Республика Сингапур (Сингапур)
* Австралия (Сидней)

### Выделим типы серверов в датацентре
* Nginx
* Backend
* Postgresql
* Redis
* Хранилища видео на SSD
* Хранилища видео на HDD

#### Конфигурация сервера Nginx
* CPU 32
* RAM 32 Gb
* SSD 256 Gb

#### Конфигурация сервера Backend
* CPU 32
* RAM 256 Gb
* SSD 256 Gb

#### Конфигурация сервера Postgresql
* CPU 32
* RAM 512 Gb
* 8 HDD дисков по 8 Tb

#### Конфигурация сервера Redis
* CPU 32
* RAM 256 Gb
* SSD 256 Gb

#### Конфигурация сервера Хранилища видео на SSD
* CPU 32
* RAM 128 Gb
* 8 SSD дисков по 8 Tb

#### Конфигурация сервера Хранилища видео на HDD
* CPU 32
* RAM 128 Gb
* 8 HDD дисков по 8 Tb

## 8. Источники <a name="8"></a>
1. https://www.globalmediainsight.com/blog/youtube-users-statistics/
2. https://exlibris.ru/news/statistika-youtube-2019-infografika/
3. https://tubularlabs.com/blog/3-metrics-youtube-success/
4. https://aws.amazon.com/ru/about-aws/global-infrastructure/regional-product-services/?p=ngi&loc=4
5. http://7youtube.ru/news/skolko-vesit-video.html
6. https://lpgenerator.ru/blog/2021/10/07/statistika-youtube-kotoruyu-nuzhno-znat-v-2021/#obshchaya-statistika-youtube-2021

