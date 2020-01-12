
 1. Запуск SUT:
* docker-compose up -d
* java -jar artifacts/app-deadline.jar -P:jdbc.url=jdbc:mysql://localhost:3306/app -P:jdbc.user=app -P:jdbc.password=pass
 2. Запуск теста
