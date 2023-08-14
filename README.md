# t-bmstu

Это агрегатор тестирующих систем.
Пока что планируется добавить следующие тестирующие системы:
* [codeforces](https://codeforces.com/)
* [Timus](https://acm.timus.ru)
* [ACMP](https://acmp.ru/)

В дальнейшем данный проект может использоваться для проведения тренировок по спортивному программированию или для выдачи индивидуального задания.

TODO дописать.

# Список участников

1. [Алексей Лисов](https://gitflic.ru/user/lisov-a2005)
2. [Егор Домаскин](https://gitflic.ru/user/desitas1701)

# Как это поднять?
Проект можно запустить с помощью `Makefile` командой `make run`. 
Или же просто запустить `/cmd/main.go` (это запустит сервер).
### Что нужно для запуска?
1) Для начала надо установить нужные библиотеки, например `Gin` 
(фреймворк для бэкенда) и `github.com/PuerkitoBio/goquery` (библиотека для парсинга),
`github.com/spf13/viper` (библиотека для парсинга yaml). 
Полный список пока приложить не могу, но все можно спокойно установить, 
открыв проект в Golang
2) Создать файл `/configs/config.yaml`. В нем должны быть следующие
Переменные
```yaml
port: "порт на котором будет запущено приложение"
DBUsername: "Имя пользователя для базы данных"
DBPassword: "Пароль для базы данных"
DBName: "Имя базы данных"
SessionSecret: "Секрет для генерации сессий"
```
Примечание: порт лучше оставить 8080, потому что позже на него будет настроена
 моя аутентификация через `github`.
3) Нужна база данных `PostgreSQL` (таблицы создадутся сами, смотреть `/database/db.go`)

### Что за странные id задач?
На самом деле id задачи это просто: `название тест системы` + 
`id задачи в этой системе` и эта строка была закодирована в `base64`

### Как присоединить новую тестирующую систему?
`/pkg/testsystems/testsystems.go` - почитать комменты там, и сразу все станет понятно

По сути для того, чтобы добавить новую тестирующую систему, необходимо:
1) Создать наследник интерфейса `TestSystem` и реализовать полностью все нужные функции
2) Добавить тестирующую систему в `AllowedTestsystems`


### Подсветка синтаксиса
https://codemirror.net/mode/