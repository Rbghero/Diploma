 # Дипломный проект по профессии «Тестировщик»
 [Задание.]()
 ## План автоматизации и отчетные документы по итогам тестирования:

[1. План автоматизации.](https://github.com/Rbghero/Diploma/blob/main/documentation/Plan.md)

[2. Отчет по итогам тестирования.](https://github.com/Rbghero/Diploma/blob/main/documentation/Report.md)

[3. Отчет по итогам автоматизации.](https://github.com/Rbghero/Diploma/blob/main/documentation/Summary.md)

 ## Процедура запуска автотестов:
 ### MySQL
1. Открыть проект в IntelliJ IDEA.
2. Запустить Docker Desktop.
3. Открыть терминал в корне проекта и запустить контейнеры командой
   `docker-compose up`.
4. Открыть второй терминал и запустить приложение **aqa-shop.jar** командой  
   `java -jar ./artifacts/aqa-shop.jar -Dspring.datasource.url=jdbc:mysql://localhost:3306/app`.
5. В отдельном терминале запустить тесты командой  
   `./gradlew clean test -DdbUrl=jdbc:mysql://localhost:3306/app`.
6. Сгенерировать отчёт Allure: `./gradlew allureServe`.
7. Остановить приложение: перейти в терминал, в котором оно запущено, и нажать **CTRL + C**.
8. Остановить контейнеры: `docker-compose down`.

 ### PostgresSQL
1. Открыть проект в IntelliJ IDEA.
2. Запустить Docker Desktop.
3. Открыть терминал в корне проекта и запустить контейнеры командой
   `docker-compose up`.
4. Открыть второй терминал и запустить приложение **aqa-shop.jar** командой  
   `java -jar ./artifacts/aqa-shop.jar -Dspring.datasource.url=jdbc:postgresql://localhost:5432/app`.
5. В отдельном терминале запустить тесты командой  
   `./gradlew clean test -DdbUrl=jdbc:postgresql://localhost:5432/app`.
6. Сгенерировать отчёт Allure: `./gradlew allureServe`.
7. Остановить приложение: перейти в терминал, в котором оно запущено, и нажать **CTRL + C**.
8. Остановить контейнеры: `docker-compose down`.
