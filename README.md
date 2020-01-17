[![Build status](https://ci.appveyor.com/api/projects/status/svsmx0kpf5pil8r2?svg=true)](https://ci.appveyor.com/project/Alexander43884/sql8)
### Тестирование функции получения СМС-кода из базы данных при авторизации на странице

---
* Создать папку, открыть терминал по адресу папки и инициализировать систему Git: `git init`
* Склонировать репозиторий: `git clone https://github.com/AlexanderKachalov/SQL8-.git`
* Перейти в директорию с проектом: `cd /SQL8-`
***
Первый запуск SUT
***
* Выполнить команду: `docker-compose up -d`
* Подождать инициализацию базы данных (1-2 минуты)
* Выполнить команду: `java -jar artifacts/app-deadline.jar -P:jdbc.url=jdbc:mysql://localhost:3306/app -P:jdbc.user=app -P:jdbc.password=pass`
* Запустить тест командой: `./gradlew test` (`./gradlew.bat test` для Windows)
* Отчет о выполнении тестов в директории: `build/reports/tests/test`
***
Второй и последующие запуски SUT
***
* Очистить базу данных командой: `docker-compose exec mysql mysql -h 127.0.0.1 -P 3306 -u app -ppass -e "delete from card_transactions; delete from auth_codes; delete from cards; delete from users;" app`
* Выполнить команду: `java -jar artifacts/app-deadline.jar -P:jdbc.url=jdbc:mysql://localhost:3306/app -P:jdbc.user=app -P:jdbc.password=pass`
* Запустить тест: `./gradlew test` (`./gradlew.bat test` для Windows)

