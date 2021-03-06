
**Для начала необходимо пройти [Типичную последовательность](index.md#_1)**

*****

### Получение данных о заказе

**Запросите данне о заказе и сумме оплаты**

Для запроса данных по заказу потребуется либо user_session, с которым был сделан заказ (если заказ делали вы сами), 
либо пин­код, если клиент пришёл с уже готовым заказом (пинкод приходит клиенту в sms и email’е при оформлении заказа 
в нашей системе вместе с информацией о заказе). 

При создании заказа на тестовом сервере ­ никаких уведомлений не приходит. Для тестов
используйте пинкод 9876, который подходит ко всем заказам (только для poligon.cultserv.ru)

Запрос информации о текущем заказе:
``http://poligon.cultserv.ru/jtransport/partner/get_current_order?session=123&user_session=abc&extended=true``

Запрос информации о заказе, если известен его номер и user_session:
``http://poligon.cultserv.ru/jtransport/partner/get_order?session=123&id=347642&user_session=abc&extended=true``

Запрос информации о заказе, если известен его номер и пин­код:
``http://poligon.cultserv.ru/jtransport/partner/get_order_for_print?id=347642&session=123&pincode=9876``

````
{
  "message": {
    "id": 12097256,
    "name": "Иванов Иван Иванович",
    "status": 2,
    "date": 1413665693542,
    "subevents": [],
    "amount": 2200,
    "epay": true,
    "frontend_id": 216,
    "eticket": false,
    "paid": false,
    "tickets" : [...]
    "totals": {
      "amount": 2000,
      "comission": 200,
      "total": 2200
    },
    "is_mine": false,
    "formulaOrder": false
  },
  "code": 1,
  "ts": 1413905365000,
  "api": 2.1
}
````

В результате возвращается полная информация по билетам (событие, секторы, места), факт
оплаты (поле paid) и информация по стоимости билета (объект totals), в котором указана
стоимость заказа (amount), комиссия (comission) и сумма стоимости с комиссией (total), которую
надо получить с клиента, если заказ не оплачен.

**NB:** Поле amount встречается дважды ­ в первичном объекте, и во вложенном объекте totals. Для
вывода стоимости ­ используйте только данные объекта totals.

*****

### Оплата

**Примите оплату и уведомите систему о принятой сумме**

Метод: paymentsAccept
[Документация](http://api.cultserv.ru/public/docs/methods/#!/categories/getCategories_get_0)

Пример использования: ``http://poligon.cultserv.ru/jtransport/partner/payments/accept?session=123&order_id=123&amount=123``

*****

### Присвоение БСО и печать билета

**Назначаете БСО**

Метод: assignBso
Пример использования: ``http://poligon.cultserv.ru/jtransport/partner/assign_bso?session=123&id=123&bso=AA005501``

**NB:** Используйте латинские буквы для указания БСО

После назначения БСО, билет считается отпечатанным на этом бланке.

*****

### Получение данных о билете

Пример использования: ``http://poligon.cultserv.ru/ticket/41b2c704-a859-4ccf-84c8-cf4ddb705e95?session=123``

Может принимать опциональные параметры:

* ``format`` - формат документа

    * ``PDF`` (указан по умолчанию)

    * ``FOP``
    
* ``document_size`` - размер печатного листа в мм (напр. ``document_size=210,290``)

* ``ticket_size`` - размер билета в мм (напр. ``ticket_size=210,290``)

* ``document_margin`` - смещение печатной области документа в мм (напр. ``document_margin=50,50``)

* ``ticket_margin`` - смещение печатной области билета в мм (напр. ``ticket_margin=15,15``)

* ``rotation`` - угол поворота кратный 90 [...-90, 0, 90, 180...]


**NB:** На полигоне билет по токену будет доступен постоянно, а на основном сервере только единожды!!!

*****

### Браковка печати

**В случае неуспешной печати билетов необходимо уведомить об этом систему.**

Метод: markBlankDefect

Пример использования: ``http://poligon.cultserv.ru/jtransport/partner/mark_blank_defect?session=123&id=123&bso=AA005501``

Передавайте те же самые значения, что и при вызове метода [assignBso](print.md#_3).