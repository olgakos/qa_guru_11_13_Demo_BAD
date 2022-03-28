# Проект по автоматизации тестирования сайта:
:earth_americas: https://itigris.com

## Содержание:
- [x] [Технологии и инструменты](#watermelon-технологии-и-инструменты)
- [x] [Реализованные проверки](#watermelon-Реализованные-проверки)
- [x] [Сборка в Jenkins](#watermelon-Jenkins-job)
- [x] [Запуск из терминала](#watermelon-Запуск-тестов-из-терминала)
- [x] [Allure отчет](#watermelon-Allure-отчет)
- [x] [Отчет в Telegram](#watermelon-Уведомление-в-Telegram-при-помощи-бота)
- [x] [Видео примеры прохождения тестов](#watermelon-Примеры-видео-о-прохождении-тестов)

## :watermelon: Технологии и инструменты

<p align="center">
<a href="https://www.jetbrains.com/idea/"><img src="images/logo/Idea.svg" width="50" height="50"  alt="IDEA"/></a>
<a href="https://www.java.com/"><img src="images/logo/Java.svg" width="50" height="50"  alt="Java"/></a>
<a href="https://github.com/"><img src="images/logo/GitHub.svg" width="50" height="50"  alt="Github"/></a>
<a href="https://junit.org/junit5/"><img src="images/logo/Junit5.svg" width="50" height="50"  alt="JUnit 5"/></a>
<a href="https://gradle.org/"><img src="images/logo/Gradle.svg" width="50" height="50"  alt="Gradle"/></a>
<a href="https://selenide.org/"><img src="images/logo/Selenide.svg" width="50" height="50"  alt="Selenide"/></a>
<a href="https://aerokube.com/selenoid/"><img src="images/logo/Selenoid.svg" width="50" height="50"  alt="Selenoid"/></a>
<a href="https://github.com/allure-framework/allure2"><img src="images/logo/Allure.svg" width="50" height="50"  alt="Allure"/></a>
<a href="https://www.jenkins.io/"><img src="images/logo/Jenkins.svg" width="50" height="50"  alt="Jenkins"/></a>
</p>

<p align="center">
<img width="6%" title="IntelliJ IDEA" src="images/logo/Intelij_IDEA.svg">
<img width="6%" title="Java" src="images/logo/Java.svg">
<img width="6%" title="Selenide" src="images/logo/Selenide.svg">
<img width="6%" title="Selenoid" src="images/logo/Selenoid.svg">
<img width="6%" title="Allure Report" src="images/logo/Allure_Report.svg">
<img width="6%" title="Gradle" src="images/logo/Gradle.svg">
<img width="6%" title="JUnit5" src="images/logo/JUnit5.svg">
<img width="6%" title="GitHub" src="images/logo/GitHub.svg">
<img width="6%" title="Jenkins" src="images/logo/Jenkins.svg">
<img width="6%" title="Telegram" src="images/logo/Telegram.svg">
</p>

Перечень технологий и инструментом, использованных при реализации этого проекта:

- автотесты написаны на языке `Java`
- для UI-тестов используется тестовый фреймворк `Selenide`
- Для сборки проекта используется `Gradle`
- Библиотека для модульного тестирования: `JUnit 5` 
- `Selenoid` демонстрирует пример запуска браузеров в контейнерах Docker (и записывает видео).
- `Jenkins` выполняет удаленный запуск тестов в визуальном-онлайн интерфейсе. Установки дополнительных приложений на компьютер пользователя не требуется. 
- `Allure Report` формирует наглядный графический отчет о результатах  запуска тестов.
- После завершения прогона тестов, специальный `Telegram Bot` отправляются в `Telegram` краткий вариант Allure Report 

## :watermelon: Реализованные проверки (Примеры UI тестов)
- провекрка текста 
- ✓ запоелнре формы обратной связи
- поиск товара в каталоге

## :watermelon: Запуск тестов из терминала

Шаги:
1. Перейтиде в комнадную строку терминала (Можно использовать терминал, встроенный в среду разработки, термнал вашего компьютра)
2. Запустите на выполение команду:

###### Локальный запуск:
```
gradle clean test
```

###### Удаленный запуск:
```
clean
test
-Dbrowser=${BROWSER}
-DbrowserVersion=${BROWSER_VERSION}
-DbrowserSize=${BROWSER_SIZE}
-DremoteDriverUrl=https://user1:1234@${REMOTE_BROWSER}/wd/hub/
-DvideoStorage=https://${REMOTE_BROWSER}/video/
-Dthreads=${THREADS}
```

## :watermelon: Запуск тестов (сборка) в Jenkins с параметрами


Шаги:
1. Перейдите на страницу сборки тестового проекта по ссылке: <a target="_blank" href="https://jenkins.autotests.cloud/job/qa_guru_11_13_Demo/">Jenkins</a>
2. Перечисленные ниже параметры можно менять прямо в графическом интерфейсе.
3. Запустите выполение тестов кнопкой "Собрать с параметрами" 

- `BROWSER` – браузер, в котором будут выполняться тесты (по умолчанию - chrome).
- `BROWSER_VERSION` версия браузера, в которой будут выполняться тесты (по умолчанию - 91.0).
- `BROWSER_SIZE` – размер окна браузера, в котором будут выполняться тесты (по умолчанию - 1920x1080).
- `REMOTE_BROWSER` - (REMOTE_URL, remoteUrl ) – адрес (логин и пароль) удаленного сервера (Selenoid), на котором будут запускаться тесты.
- `THREADS` - кол-во потоков

Параметры для выгрузки Telegram Bot:
- `PROJECT_NAME`  название проекта
- `ENVIRONMENT` - тестовый стенд (prod, preprod, stage...), на котором запускались тесты. В данном случае информация не задана. 
- `BUILD_URL` - ссылка на сборку
- `COMMENT` - текстовой комментарий

 ## :watermelon: Allure отчет
 
После того, как тесты запущены на выполение и завершлись, можно получить визуальный Allure отчет. Это можно сделать разными способами.
1. Найти ссылку в среде разработки IDEA (в папке Allure Serve)
Или:
2.1 Выполнить сборку в Jenkins
2.2. Убедиться, что в блоке История сборок напротив номера сборки появился значок Allure Report
2.3 Кликнуть по  значку Allure Report
Ожидаемый результат: Откроется страница с готовым Allure-отчетом

###### Главная страница Allure-отчета содержит следующие информационные блоки:

- `ALLURE REPORT` отображает: Дату и время прохождения теста. Общее количество пройденных кейсов. Диаграмму с указанием процента и количества успешных, упавших и сломавшихся в процессе выполнения тестов
- `TREND` - отображает тренд прохождения тестов от сборки к сборке
- `SUITES` - отображает распределение результатов тестов по тестовым наборам
- `ENVIRONMENT` - отображает тестовое окружение (стенд), на котором запускались тесты. В данном случае информация не задана.
- `CATEGORIES` - отображает распределение неуспешно прошедших тестов по видам дефектов !!!!!!!!!!!!!!!!!!!
- `FEATURES BY STORIES` - отображает распределение тестов по функционалу, который они проверяют !!!!!!!!!!!!!!!!
- `EXECUTORS` - отображает исполнителя текущей сборки (ссылка на сборку в Jenkins) !!!!!!!!!!!!!

<p align="center">
<img title="Allure Graphics" src="images/screens/Screenshot_ХХХ.png">
</p>

## :watermelon:  Видео прохождения тестов на Selenoid
К каждому тесту в отчете прилагается автоматически сгенерирвоанное видео. Пример видео:

<p align="center">
<img title="Видео прохождения тестов на Selenoid" src="images/screens/Screenshot_ХХХ.png">
</p>

## :bellhop_bell: <img src="images/logo/Telegram.svg" width="25" height="25"  alt="Telegram"/></a> Уведомление в Telegram при помощи бота
После завершения сборки специальный Telegram-бот, автоматически обрабатывает и отправляет сообщение с отчетом о прогоне тестов.
Чтобы после запуска тестов получть уведомление, встепите в групп ***

<p align="center">
<img title="Telegram Bot" src="images/screens/Screenshot_ХХХ.png">
</p>

----------------------------------
Here is a simple footnote[^1].

A footnote can also have multiple lines[^2].  

You can also use words, to fit your writing style more closely[^note].

[^1]: My reference.
[^2]: Every new line should be prefixed with 2 spaces.  
  This allows you to have a footnote with multiple lines.
[^note]:
    Named footnotes will still render with numbers instead of the text but allow easier identification and linking.  
    This footnote also has been made with a different syntax using 4 spaces for new lines.
