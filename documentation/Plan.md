# Перечень автоматизируемых сценариев
## Сценарии для формы "Оплата по карте" и Payment Gate
UI
1. Успех при заполнении формы “Оплата по карте” валидными данными, одобренная карта (happy path).
Ожидаемый результат: сообщение об успехе, появление новых записей в БД (таблицы payment_entity, order_entity).

2. Отказ при заполнении формы “Оплата по карте” валидными данными, отклоненная карта (sad path).
Ожидаемый результат: сообщение об успехе, появление новых записей в БД (таблицы payment_entity, order_entity).

3. Отправка формы с пустым полем “Номер карты”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

4. Отправка формы с буквенными значениями в поле “Номер карты”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

5. Отправка формы с 15 цифрами в поле “Номер карты”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

6. Отправка формы с 17 цифрами в поле “Номер карты”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

7. Отправка формы с 16 случайными цифрами в поле “Номер карты”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об отказе.

8. Отправка формы с пустым полем “Месяц”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

9. Отправка формы с невалидным (“00”) значением поля “Месяц”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

10. Отправка формы с невалидным (“13”) значением поля “Месяц”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

11. Отправка формы с пустым полем “Год”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

12. Указать текущий месяц в поле “Месяц” и текущий год в поле “Год”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об успехе.

13. Указать +4 года от текущего года в поле “Год”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об успехе.

14. Указать +5 лет от текущего года в поле “Год”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об успехе.

15. Указать +6 лет от текущего года в поле “Год”, остальные поля заполнены валидными данными.
Ожидаемый результат: Сообщение об ошибке.

16. Указать прошедший год в поле “Год”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

17. Указать прошедший месяц в поле “Месяц” и текущий год в поле “Год”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

18. Отправка формы с пустым полем “Владелец”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

19. Указать значение на латинице (“Ivan Ivanov”) в поле “Владелец”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об успехе.

20. Указать значение на латинице с использованием дефиса (“Ivan Ivanov-Petrov”) в поле “Владелец”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об успехе.

21. Отправка формы со значением на кириллице (“Иван Иванов”) в поле “Владелец”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

22. Отправка формы с цифрами (“Ivan Ivan0v”) в поле “Владелец”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

23. Отправка формы со спецсимволами (“Ivan Ivan%v”) в поле “Владелец”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

24. Отправка формы с пустым полем “CVC/CVV”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

25. Клик по кнопке “Продолжить” без заполнения полей.
Ожидаемый результат: все поля подсветились красным, под каждым полем появилось сообщение об ошибке, форма не отправляется.

API

26. Отправка POST-запроса на URL http://localhost:9999/payment с валидными данными в body, одобренная карта.
Ожидаемый результат: статус 200 OK.

27. Отправка POST-запроса на URL http://localhost:9999/payment с валидными данными в body, отклоненная карта.
Ожидаемый результат: статус 200 OK.

28. Отправка POST-запроса на URL http://localhost:9999/payment с пустым body.
Ожидаемый результат: Статус 400 Bad Request.

29. Отправка POST-запроса на URL http://localhost:9999/payment с пустым значением “number” (“year”, “month”, “holder” и “cvc” заполнены валидными данными).
Ожидаемый результат: Статус 400 Bad Request.

30. Отправка POST-запроса на URL http://localhost:9999/payment с пустым значением “year” (“number”, “month”, “holder” и “cvc” заполнены валидными данными).
Ожидаемый результат: Статус 400 Bad Request.

31. Отправка POST-запроса на URL http://localhost:9999/payment с пустым значением “month” (“number”, “year”, “holder” и “cvc” заполнены валидными данными).
Ожидаемый результат: Статус 400 Bad Request.

32. Отправка POST-запроса на URL http://localhost:9999/payment с пустым значением “holder” (“number”, “year”, “month” и “cvc” заполнены валидными данными).
Ожидаемый результат: Статус 400 Bad Request.

33. Отправка POST-запроса на URL http://localhost:9999/payment с пустым значением “cvc” (“number”, “year”, “month” и “holder” заполнены валидными данными).
Ожидаемый результат: Статус 400 Bad Request.

## Сценарии для формы "Купить в кредит" и Credit Gate

UI
1. Успех при заполнении формы “Купить в кредит” валидными данными, одобренная карта (happy path).
Ожидаемый результат: появление новых записей в БД (credit_request_entity, order_entity).

2. Отказ при заполнении формы “Купить в кредит” валидными данными, отклоненная карта (sad path).
Ожидаемый результат: появление новых записей в БД (credit_request_entity, order_entity).

3. Отправка формы с пустым полем “Номер карты”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

4. Отправка формы с буквенными значениями в поле “Номер карты”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

5. Отправка формы с 15 символами в поле “Номер карты”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

6. Отправка формы с 17 символами в поле “Номер карты”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

7. Отправка формы с 16 случайными цифрами в поле “Номер карты”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об отказе.

8. Отправка формы с пустым полем “Месяц”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

9. Отправка формы с невалидным (“00”) значением поля “Месяц”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

10. Отправка формы с невалидным (“13”) значением поля “Месяц”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

11. Отправка формы с пустым полем “Год”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

12. Указать текущий месяц в поле “Месяц” и текущий год в поле “Год”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об успехе.

13. Указать +4 года от текущего года в поле “Год”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об успехе.

14. Указать +5 лет от текущего года в поле “Год”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об успехе.

15. Указать +6 лет от текущего года в поле “Год”, остальные поля заполнены валидными данными.
Ожидаемый результат: Сообщение об ошибке.

16. Указать прошедший год в поле “Год”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

17. Указать прошедший месяц в поле “Месяц” и текущий год в поле “Год”.
Ожидаемый результат: сообщение об ошибке.

18. Отправка формы с пустым полем “Владелец”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

19. Указать значение на латинице (“Ivan Ivanov”) в поле “Владелец”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об успехе.

20. Указать значение на латинице с использованием дефиса (“Ivan Ivanov-Petrov”) в поле “Владелец”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об успехе.

21. Отправка формы со значением на кириллице (“Иван Иванов”) в поле “Владелец”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

22. Отправка формы с цифрами (“Ivan Ivan0v”) в поле “Владелец”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

23. Отправка формы со спецсимволами (“Ivan Ivan%v”) в поле “Владелец”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

24. Отправка формы с пустым полем “CVC/CVV”, остальные поля заполнены валидными данными.
Ожидаемый результат: сообщение об ошибке.

25. Клик по кнопке “Продолжить” без заполнения полей. 
Ожидаемый результат: все поля подсветились красным, под каждым полем появилось сообщение об ошибке, форма не отправляется.

API

26. Отправка POST-запроса на URL http://localhost:9999/credit с валидными данными в body, одобренная карта.
Ожидаемый результат: статус 200 OK.

27. Отправка POST-запроса на URL http://localhost:9999/credit с валидными данными в body, отклоненная карта.
Ожидаемый результат: статус 200 OK.

28. Отправка POST-запроса на URL http://localhost:9999/credit с пустым body.
Ожидаемый результат: Статус 400 Bad Request.

29. Отправка POST-запроса на URL http://localhost:9999/credit с пустым значением “number” (“year”, “month”, “holder” и “cvc” заполнены валидными данными).
Ожидаемый результат: Статус 400 Bad Request.

30. Отправка POST-запроса на URL http://localhost:9999/credit с пустым значением “year” (“number”, “month”, “holder” и “cvc” заполнены валидными данными).
Ожидаемый результат: Статус 400 Bad Request.

31. Отправка POST-запроса на URL http://localhost:9999/credit с пустым значением “month” (“number”, “year”, “holder” и “cvc” заполнены валидными данными).
Ожидаемый результат: Статус 400 Bad Request.

32. Отправка POST-запроса на URL http://localhost:9999/credit с пустым значением “holder” (“number”, “year”, “month” и “cvc” заполнены валидными данными).
Ожидаемый результат: Статус 400 Bad Request.

33. Отправка POST-запроса на URL http://localhost:9999/credit с пустым значением “cvc” (“number”, “year”, “month” и “holder” заполнены валидными данными).
Ожидаемый результат: Статус 400 Bad Request.

### Перечень используемых инструментов с обоснованием выбора
- Язык программирования: Java.
- Среда разработки: IntelliJ IDEA.
- Система сборки: Gradle – простое настраивание зависимостей, более удобная структура build.gradle по сравнению с pom.xml у Maven.

### Библиотеки и фреймворки:
* Фреймворк для тестирования JUnit Jupiter – имеется опыт работы в предыдущих проектах.
* Selenide – более широкий в сравнении с Selenium функционал, упрощенная работа с элементами, также не требует дополнительных настроек. 
* DbUtils для упрощения взаимодействий с СУБД.
* Java Faker для генерации тестовых данных.
* REST Assured для тестирования API.
* Lombok – позволяет сократить код и улучшить его читабельность, а также позволяет не прописывать вручную однотипные шаблонные участки кода, что сохраняет время и минимизирует возможные ошибки.
* Allure Report для составления отчетов. Достаточно легко интегрируется в проект, генерирует демонстративные отчеты.

### Перечень и описание возможных рисков при автоматизации
- Отсутствие технической документации и требований к продукту не позволяет корректно определить и сформулировать ожидаемое поведение программы, также в условиях отсутствия документации можно “упустить” важные проверки.
- Настройка SUT может вызвать трудности и занять дополнительное время (подключение СУБД, gate-simulator, запуск jar-файла).
- В случае изменения веб-элементов на странице возникнет необходимость править тесты.
- Значения полей “Месяц” и “Год” нельзя вписывать прямо в автотесты, они должны изменяться с течением времени, иначе тесты будут становиться неактуальными, и будут требовать постоянных правок.
- Поскольку тестирование проводится на симуляторе, есть риск возникновения новых дефектов при подключении к реальным банковским сервисам.
- Увеличенное по сравнению с ручным тестированием время выполнения.

### Интервальная оценка с учётом рисков (в часах)
- Настройка SUT – 6 часов.
- Создание необходимых классов (дата-генераторы,PageObject) – 6 часов.
- Написание автотестов и их прогон – 24-48 часов.
- Создание баг-репортов – 5 часов.
- Подготовка отчетной документации – 4 часа.
- Всего 45-69 часов.

### План сдачи работ (когда будут авто-тесты, результаты их прогона и отчёт по автоматизации)
* Автотесты будут готовы к 20.07.2023.
* Баг-репорты и отчёты по результатам тестов будут готовы 23.07.2023.
* Отчет по результатам автоматизации будет готов 23.07.2023.