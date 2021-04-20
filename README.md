# airlines-tickets
Airlines tickets

#Deploy project
```
docker-compose build
docker-compose up -d
docker exec -it airline_api sh docker/init.sh
```

#### Deploy symfony project (if you don't have docker!)

###### __Update composer__
```bash
composer self-update

```

###### __Install dependencies composer__
```bash
composer install

```

###### __Create database__
```bash
php bin/console doctrine:database:create

```

###### __Make migrations__
```bash
php bin/console doctrine:migrations:migrate

```
###### __Load fixtures__
```bash
php bin/console doctrine:fixtures:load --append

### Тестовое задание для Middle Back-end Developer (PHP):

Реализовать небольшое API для авиакомпании. API реагирует на следующие запросы-команды пользователя:

забронировать место в рейсе;

отменить бронь;

купить билет;

возвратить купленный билет.


Место - обычное число от 1 до 150. Купить билет можно как после бронирования, так и без него.

Функционал оплаты и возврата денег реализовывать не нужно, достаточно изменить состояние.

Следует считать, что API подписан на получение событий через HTTP протокол (callback-уведомления) на один из своих адресов. К примеру, http://localhost/api/v1/callback/events.

Типы уведомлений:
завершена продажа билетов на рейс;
рейс отменён.

Пример уведомления:
{"data":{"flight_id":1,"triggered_at":1585012345,"event":"flight_ticket_sales_completed","secret_key":"a1b2c3d4e5f6a1b2c3d4e5f6"}}

При отмене рейса пользователям, забронировавшим или купившим билеты на этот рейс, в фоновом режиме (асинхронно) отправляются эл. письма об отмене рейса. В случае ответа на событие HTTP кодом отличным от 200 событие будет повторно получено через некоторый промежуток времени.

Условия реализации
Symfony 4+;
PHP 7.3;
в качестве хранилища — что угодно (БД, память и т.д.);
добавить инструкцию по сборке/запуску проекта;
результат выложить на Github/Gitlab.
