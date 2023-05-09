# daemon_cron
My first custom cron-daemon pair without using java.util.concurrent to execute jobs in multithread environment.

1. Описание репозитория и daemon.

Данный репозиторий содержит 2 архива:
- Cron-master.zip (архив с крон-приложением клиента)
- daemon-master.zip (архив с демоном)

Демон способен выполнять задачи (методы) при следуюших условиях:
- класс имеет публичный конструтор по умолчанию
- метод класса публичный
- метод не имеет выходных параметров

2. Сборка и запуск приложений.
2.1. Распаковываем скачанные архивы
2.2. Переименовываем полученные корневые папки в Cron и daemon соответственно 
2.3. Из папки Cron (аналогично для daemon) запускаем команду mvn clean install
2.4. Переходим на уровень выше командой cd target
2.5.1. Для Cron выполняем кодманду:
java -jar Cron-1.0-SNAPSHOT.jar
2.5.2. Для daemon выполняем кодманду:
java -jar daemon-1.0-SNAPSHOT-jar-with-dependencies.jar

3. Проверка работы приложения.

В консоли Cron приложения можно проверить работу Cron и daemon при помощи следующих команд:
- создание задачи:
<путь к фалу .jar> <имя класса> <имя метода без круглых скобок> <крон-расписание>
(пример)
C:/IdeaProjects/test_jar_1/target/test_jar_1-1.0-SNAPSHOT.jar org.example.main updateDB "0/5 * * ? * *"
- удаление задач:
remove <путь к фалу .jar> <имя класса> <имя метода без круглых скобок>
(пример)
remove C:/IdeaProjects/test_jar_1/target/test_jar_1-1.0-SNAPSHOT.jar org.example.main sendNotification
- выход из Cron:
exit

В файле logs/app.log демона можно посмотреть выполненные операции.
