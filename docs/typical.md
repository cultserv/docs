
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

Метод: sector/get

Возвращает информацию, необходимую для построения матрицы зала, и информацию о доступных билетах и их стоимости.

Пример использования: ``http://poligon.cultserv.ru/v4/sector/get?session=123&sector_id=123&subevent_id=123&user_session=abc``

````
{
  "message": {
    "id": 149,
    "title": "VIP left 1",
    "content": [
      {
        "r": "1",
        "n": "1",
        "t": 1,
        "x": 0,
        "y": 0,
        "id": 5845068,
        "s": 0,
        "m": false,
        "p": 6000
      },
      {
        "r": "1",
        "n": "8",
        "t": 1,
        "x": 6,
        "y": 2,
        "id": null,
        "s": 2,
        "m": false,
        "p": null
      },
      {...}
    ]
  },
  "code": 1,
  "ts": 1414599159645,
  "version": "2.1"
}
````

Где:

* ``id`` - ID сектора

* ``title`` - Имя сектора

    * ``content`` - информация о местах

        * ``r`` - номер ряда

        * ``n`` - номер места

        * ``t`` - тип места (Справочник: ``seatType/list``)

        * ``x`` - координата по горизонтали

        * ``y`` - координата по вертикали

        * ``s`` - статус места
            
            * ``0`` - доступно
            
            * ``1`` - в корзине (если ``m`` - true, то в корзине именно этого пользователя по ``user_session``)
            
            * ``любой другой`` - недоступно
            
        * ``m`` - флаг принадлежности текущему пользователю (по ``user_session``)

        * ``id`` - ID билета
        
        * ``p`` - цена билета
            
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