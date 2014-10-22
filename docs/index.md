### Запрос событий

**Запросить список доступных категорий**

Метод: getCategories
[Документация](http://api.cultserv.ru/public/docs/methods/#!/categories/getCategories_get_0)

Пример использования: ``http://poligon.cultserv.ru/jtransport/partner/get_categories?session=123``

*****

**Или запросить список актуальных событий**

Метод: getActualEventsIdsOnly

Пример использования: ``http://poligon.cultserv.ru/jtransport/partner/get_actual_events_ids_only?session=123``

Метод возвращает исключительно ID событий.
Может принимать опциональный параметр ``etickets_only``

Пример использования: ``http://poligon.cultserv.ru/jtransport/partner/get_actual_events_ids_only?session=123&etickets_only=true``

*****

**Используя id категории получить список доступных событий для категории**

Метод: getEvents
[Документация](http://api.cultserv.ru/public/docs/methods/#!/events/getEvents_get_3)

Пример использования: ``http://poligon.cultserv.ru/jtransport/partner/get_events?session=123&category=8``

*****

**Используя id события получить детальное описание события**

Метод: getSubevent
[Документация](http://api.cultserv.ru/public/docs/methods/#!/events/getSubevent_get_5)

Пример использования: ``http://poligon.cultserv.ru/jtransport/partner/get_subevent?session=123&id=123``

*****

### Добавление билетов в корзину

**Сгенерировать пользовательскую сессию**

Метод: generateUserSession
[Документация](http://api.cultserv.ru/public/docs/methods/#!/user/generateUserSession_get_0)

Пример использования: ``http://poligon.cultserv.ru/jtransport/partner/generate_user_session?session=123``

*****

**В детальном описании события выбрать сектор из которого будут добавляться билеты**

*****

**Если признак сектора admission : true - это входные билеты, такие билеты можно сразу добавлять в корзину, указав необходимое количество и цену билета***

Метод: addAdmission
[Документация](http://api.cultserv.ru/public/docs/methods/#!/cart/addAdmission_get_0)

Пример использования: ``http://poligon.cultserv.ru/jtransport/partner/add_admission?session=123&subevent_id=123&sector_id=123&price=123&count=1&user_session=abc``

*****

**Если признак сектора admission : false - это билеты с местами, в этом случае надо запросить список доступных билетов и после добавить выбранные билеты в корзину**

Метод: getSectorWithTickets

Возвращает информацию, необходимую для построения матрицы зала, и информацию о доступных билетах и их стоимости.

Пример использования: ``http://poligon.cultserv.ru/jtransport/partner/get_sector_with_tickets?sector_id=123&session=123&subevent_id=123&user_session=abc``

````
{
  "message": {
    "id": 123,
    "title": "Партер",
    "count": 42,
    "content": [
      {
        "number": 9,
        "seats": [
          {
            "n": 0,
            "s": 2,
            "m": 0,
            "p": 0
          },
          {
            "id": 6505869,
            "n": 68,
            "s": 1,
            "m": 1,
            "p": 4500
          },
          {...}
        ]
      },
      {
        "number": 10,
        "seats": [
          {...},
          {
            "n": 0,
            "s": 2,
            "m": 0,
            "p": 0
          },
          {
            "id": 6505869,
            "n": 68,
            "s": 1,
            "m": 1,
            "p": 4500
          },
          {...}
        ]
      }
    ],
    "gateway_id": 1
  },
  "code": 1,
  "ts": 1413980609186,
  "api": 2.1
}
````

Где:

* ``content[i]`` - информация о ряде

    * ``number`` - номер ряда

    * ``seats[i]`` - информация о месте

        * ``id`` - ID места (если поля нет, значит в этой ячейке матрицы место отсутствует)

        * ``n`` - номер места, если n = 0, в этой ячейке матрицы место отсутствует

        * ``s`` - статус места

            * 0 - доступно

            * 1 - в корзине

            * любой другой - недоступно

        * ``m``

            * 0 - не принадлежит текущему пользователю

            * 1 - принадлежит

        * ``p`` - цена

- - -

Метод: addTicket
[Документация](http://api.cultserv.ru/public/docs/methods/#!/cart/addTicket_get_1)

Пример использования: ``http://poligon.cultserv.ru/jtransport/partner/add_ticket?session=123&ticket_id=123&user_session=abc&subevent_id=123&sector_id=123``

*****

### Оформление заказа

**Добавив билеты в корзину - можно указать данные пользователя**

Метод: updateOrder
[Документация](http://api.cultserv.ru/public/docs/methods/#!/order/makeOrder_get_3)

Пример использования: ``http://poligon.cultserv.ru/jtransport/partner/update_order?session=123&user_session=abc&name=Abc&phone=79291234567``

*****

**Получить список способов оплаты**

Метод: getTypeOfPayment
[Документация](http://api.cultserv.ru/public/docs/methods/#!/order/getTypeOfPayment_get_8)

Пример использования: ``http://poligon.cultserv.ru/jtransport/partner/get_type_of_payment?session=123&user_session=abc``

*****

**Указать способ оплаты***

Метод: setTypeOfPayment
[Документация](http://api.cultserv.ru/public/docs/methods/#!/order/setTypeOfPayment_get_9)

Пример использования: ``http://poligon.cultserv.ru/jtransport/partner/set_type_of_payment?session=123&id=123&user_session=abc``

*****

**Получить список способов получения билетов**

Метод: getTypeOfSale
[Документация](http://api.cultserv.ru/public/docs/methods/#!/order/getTypeOfSale_get_6)

Пример использования: ``http://poligon.cultserv.ru/jtransport/partner/get_type_of_sale?session=123&user_session=abc``

*****

**Указать способ получения билетов**

Метод: setTypeOfSale
[Документация](http://api.cultserv.ru/public/docs/methods/#!/order/setTypeOfSale_get_7)

Пример использования: ``http://poligon.cultserv.ru/jtransport/partner/set_type_of_sale?session=123&id=123&user_session=abc``

*****

**Если пользователь готов оформить заказ - финализировать его**

Метод: finishOrder
[Документация](http://api.cultserv.ru/public/docs/methods/#!/order/finishOrder_get_4)

Пример использования: ``http://poligon.cultserv.ru/jtransport/partner/finish_order?session=123&user_session=abc``