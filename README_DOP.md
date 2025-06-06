# Итоговая проверочная работа

---

#### Дополнительное задание

* Все исполняемые файлы расположены в папке ./bin
* Файлы миграций базы данных расположены в папке ./migrations
* Миграции представлены в формате утилиты __migrate__. Если вы будете использовать другую утилиту миграций, тогда вам необходимо самостоятельно преобразовать файлы миграций в формат выбранной вами утилиты.

---

1. В проекте Docker Compose нужно запустить контейнер __database__ с сервером базы данных Postgres (версия не ниже 15.0). Сервер должен принимать подключения по адресу 127.0.0.1:5432
2. В Docker контейнере __migrate-util__ нужно запустить утилиту миграции и применить команды миграции БД из папки __./migrations__
3. В Docker контейнере __storage-service__ нужно запустить исполняемый файл __./bin/storage-service__
4. Добавить правило маршрутизации запросов для __location /rpc__
   * Все запросы удовлетворяющие правилу __storage.*__ проксируются в сервис __storage-service__
5. Пример тестового запроса:

В заголовке X-Rpc-Method передаем значение "storage.getUserById"

В теле запроса передаем данные в формате JSON:
```
{
   "id":12  // возможные значения от 1 до 1000
}
```
Пример ответа:
```
{
   "ID": 12,
   "Username": "Daniel7484",
   "GivenName": "Ashley",
   "FamilyName": "Rau",
   "Email": "deangelokassulke@wolff.org"
}
```