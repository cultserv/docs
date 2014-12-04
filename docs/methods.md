### Список площадок

Метод: venues/list

Пример использования: ``http://poligon.cultserv.ru/v4/venues/list?session=123``

````
{
  "message": [
    {
      "id": 1,
      "title": "Дворец спорта «Мегаспорт»",
      "address": "Ходынский бульвар, дом 3",
      "alias": "dvorec-sporta-megasport",
      "region_id": 1,
      "type_id": 1
    },
    {
      "id": 2,
      "title": "Концертный зал «Мир»",
      "address": "Цветной бульвар, дом 11, строение 2",
      "alias": "koncertniy-zal-mir",
      "region_id": 1,
      "type_id": 3
    },
    {...}
  ],
  "code": 1,
  "ts": 1415963561542,
  "version": "2.1"
}
````

### Типы площадок

Метод: venues/list

Пример использования: ``http://poligon.cultserv.ru/v4/venues/types/list?session=123``

````
{
  "message": [
    {
      "id": 1,
      "title": "Спорт",
      "icon": "marker_4.png"
    },
    {
      "id": 2,
      "title": "Театр",
      "icon": "marker_3.png"
    },
    {...}
  ],
  "code": 1,
  "ts": 1415963561542,
  "version": "2.1"
}
````

### Оферты

Метод: offers/get

Описание: Метод, возвращающий оферту для указанной сессии (фронтенда).

Пример использования: ``http://poligon.cultserv.ru/v4/offers/get?session=123``

````
{
  "message": "<p><b>Соглашение об условиях предоставления ...</b></p>",
  "code": 1,
  "ts": 1416303912745,
  "version": "2.1"
}
````

*****

Метод: offers/event/get

Описание: Метод, возвращающий оферту для указанной группы событий.

Пример использования: ``http://poligon.cultserv.ru/v4/offers/event/get?session=123&id=123``

*****

Метод: offers/subevent/get

Описание: Метод, возвращающий оферту для указанного события.

Пример использования: ``http://poligon.cultserv.ru/v4/offers/subevent/get?session=123&id=123``

### Время брони

Метод: templates/redemption

Описание: Метод, возвращающий шаблон времени бронирования для указанной сущности.

Пример использования для события: ``http://poligon.cultserv.ru/v4/templates/redemption?subevent_id=445642&session=123``

Пример использования для заказа: ``http://poligon.cultserv.ru/v4/templates/redemption?order_id=7752917&session=123``

*****

Тестовое событие с указанным ограничением по времени выкупа: ``http://poligon.cultserv.ru/jtransport/partner/get_subevent?id=445642&session=123``