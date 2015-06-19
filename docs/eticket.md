### Получение информации о e-ticket

Метод: /jtransport/partner/get_eticket  
Параметры:

* user_session - сессия пользователя
* id - идентификатор билета

Продакшн хост: api.cultserv.ru  
Тестовый хост: poligon.cultserv.ru

Для получения информации о e-ticket у партнёра должно быть высталено право __print.eticket__

Метод назначает бланк билету, который в последствии будет доступен только тому партнёру,
который вызвал этот метод. В ответе будет содержаться поле __info.link__ со ссылкой на
готовый к печати билет в формате HTML (по умолчанию). Так же есть возможность получить e-ticket
в формате PDF. Для этого нужно присоеденить строку _".pdf"_ к ссылке на билет из поля info.link.

Пример ссылки на получение PDF e-ticket'а
`http://poligon.cultserv.ru/eticket/b2f5843b085452dbe2ff6bfd40a1ee04/35d693081e88b3e839ccb3db52901a3fa4bc8ce7.pdf`

Кроме модифицирования самой ссылки на билет, есть возможность управлять форматом билета с помощью HTTP заголовка __Accept__.
Т.е. для получения билета в формате PDF в заголовке Accept должно быть передано значение "application/pdf".

Пример JSON ответа метода:

````
{
    "api": 2.1,
    "code": 1,
    "message": {
        "admission": true,
        "barcode": "02000960571300433020",
        "blank": {
            "defect": false,
            "is_fanticket": false,
            "number": 75575,
            "number_str": "EP075575",
            "seria": "EP",
            "user_id": 686
        },
        "commission": 0,
        "id": 5446130,
        "info": {
            "attention_eng": "PGg2PkF0dGVudGlvbiE8L2g2Pg0KPHA+4oCUIFRoZSB3aG9sZSBwYWdlIGlzIGEgdGlja2V0LjwvcD4NCjxwPuKAlCBTaW5nbGUgZW50cmFuY2UgZm9yIG9uZSBwZXJzb24gaXMgcmVzb2x2ZWQuPC9wPg0KPHA+4oCUIFVubGF3ZnVsIHJlc2FsZSAob3IgYXR0ZW1wdGVkIHVubGF3ZnVsIHJlc2FsZSkgb2YgYSB0aWNrZXQgaXMgZ3JvdW5kcyBmb3Igc2VpenVyZSBvciBjYW5jZWxsYXRpb24gb2YgdGhhdCB0aWNrZXQgd2l0aG91dCByZWZ1bmQgb3Igb3RoZXIgY29tcGVuc2F0aW9uLjwvcD4NCjxwPuKAlCBJdCBpcyBwcm9oaWJpdGVkIHRvIG1ha2UgZHVwbGljYXRlcyBvZiBhIHRpY2tldC4gT25lIHRpY2tldCBmb3Igb25lIHBlcnNvbiBmb3IgYSBzaW5nbGUgZW50cmFuY2UuPC9wPg0KPHA+4oCUIFByb21vdGVyL1ZlbnVlIE93bmVyIHJlc2VydmVzIHRoZSByaWdodCB0byBkZW1hbmQgcGFzc3BvcnQgb3IgYW55IG90aGVyIElEIG9mIHRoZSB0aWNrZXQgaG9sZGVyLjwvcD4NCjxwPkNvbnRhY3QgdXM6IDggODAwIDU1NS04MC0xMTwvcD4NCjxwPlRpY2tldHMgY2FuIGJlIGV4Y2hhbmdlZCBvciByZWZ1bmRlZCBhZnRlciBwdXJjaGFzZSBpbiBjYXNlIG9mIGNhbmNlbGxlZCBhbmQgcmVzY2hlZHVsZWQgZXZlbnRzLiBUbyBleGNoYW5nZSB5b3VyIHRpY2tldHMgY29udGFjdCBMaW1pdGVkIExpYWJpbGl0eSBDb21wYW55IOKAnEt1bHR1cm5heWEgU2x1emhiYeKAnSAocmVnaXN0ZXJlZCBudW1iZXIgMTEwNzc0NjA2NTQyNiwgYWRkcmVzcyBUYWdhbnNrYXkgc3RyLiwgMjYsIGJ1aWxkLjEsIE1vc2NvdywgMTA5MTQ3LCB0ZWwuKDQ5NSkyMjgtMjA4MCkuPC9wPg==",
            "attention_rus": "PGg2PtCS0L3QuNC80LDQvdC40LUhPC9oNj4NCjxwPiAg4oCUINCS0YHRjyDRgdGC0YDQsNC90LjRhtCwINGP0LLQu9GP0LXRgtGB0Y8g0LHQuNC70LXRgtC+0LwuPC9wPg0KPHA+ICDigJQg0JLRhdC+0LQg0L3QsCDQvNC10YDQvtC/0YDQuNGP0YLQuNC1INC/0L4g0LHQuNC70LXRgtGDINCy0L7Qt9C80L7QttC10L0g0YLQvtC70YzQutC+INC+0LTQuNC9INGA0LDQtyDQuCDRgtC+0LvRjNC60L4g0L7QtNC90L7QvNGDINGH0LXQu9C+0LLQtdC60YMuPC9wPg0KPHA+ICDigJQg0J3QtSDQv9GA0LjQvtCx0YDQtdGC0LDQudGC0LUg0Y3Qu9C10LrRgtGA0L7QvdC90YvQtSDQsdC40LvQtdGC0Ysg0YEg0YDRg9C6LjwvcD4NCjxwPiAg4oCUINCd0LUg0LTQvtC/0YPRgdC60LDQudGC0LUg0LrQvtC/0LjRgNC+0LLQsNC90LjRjyDRjdC70LXQutGC0YDQvtC90L3QvtCz0L4g0LHQuNC70LXRgtCwLiDQndCwINC80LXRgNC+0L/RgNC40Y/RgtC40LUg0YHQvNC+0LbQtdGCINC/0L7Qv9Cw0YHRgtGMINGC0L7Qu9GM0LrQviDQvtC00LjQvSDRh9C10LvQvtCy0LXQuiDQv9C+INC+0LTQvdC+0LzRgyDQtS3RgtC40LrQtdGC0YMuINCU0L7Qv9GD0YHQutCw0Y8g0LrQvtC/0LjRgNC+0LLQsNC90LjQtSwg0JLRiyDRgNC40YHQutGD0LXRgtC1INC90LUg0L/QvtC/0LDRgdGC0Ywg0L3QsCDQvNC10YDQvtC/0YDQuNGP0YLQuNC1LjwvcD4NCjxwPiAg4oCUINCf0YDQuCDQv9C+0YHQtdGJ0LXQvdC40Lgg0LzQtdGA0L7Qv9GA0LjRj9GC0LjRjyDQvtGA0LPQsNC90LjQt9Cw0YLQvtGAINCy0L/RgNCw0LLQtSDQv9C+0YLRgNC10LHQvtCy0LDRgtGMINC/0YDQtdC00YrRj9Cy0LjRgtGMINC/0LDRgdC/0L7RgNGCINC40LvQuCDQuNC90L7QuSDQtNC+0LrRg9C80LXQvdGCLCDRg9C00L7RgdGC0L7QstC10YDRj9GO0YnQuNC5INC70LjRh9C90L7RgdGC0Ywg0LLQu9Cw0LTQtdC70YzRhtCwINCx0LjQu9C10YLQsC48L3A+DQo8cD7QmtC+0L3RgtCw0YLQvdGL0LUg0YLQtdC70LXRhNC+0L3RizogOCA4MDAgNTU1LTgwLTExPC9wPg==",
            "code": "262920",
            "image": "",
            "link": "http://poligon.cultserv.ru/eticket/b2f5843b085452dbe2ff6bfd40a1ee04/35d693081e88b3e839ccb3db52901a3fa4bc8ce7",
            "org_info": "0J7RgNCz0LDQvdC40LfQsNGC0L7RgDog0J7QntCeIMKr0JrRg9C70YzRgtC/0YDQvtC00YPQutGCwrsuINCzLtCh0LDQvdC60YIt0J/QtdGC0LXRgNCx0YPRgNCzLCDQv9GA0L7RgdC/0LXQutGCINCt0L3RgtGD0LfQuNCw0YHRgtC+0LIsINC00L7QvCA0Nywg0LrQvtGA0L/Rg9GBMS4g0JjQndCdOiA3ODA2NDkxNDQ1CtCQ0LPQtdC90YI6INCe0J7QniDCq9Ca0YPQu9GM0YLRg9GA0L3QsNGPINGB0LvRg9C20LHQsMK7LiAxMDkxNDcsINCzLtCc0L7RgdC60LLQsCwg0YPQuy7QotCw0LPQsNC90YHQutCw0Y8sINC0LjI2LCDRgdGC0YAuMS4g0JjQndCdOiA3NzA3NzE5Mjk3CtCj0YLQstC10YDQttC00LXQvdC+INC/0YDQuNC60LDQt9C+0Lwg0LzQuNC90LjRgdGC0LXRgNGB0YLQstCwINCa0YPQu9GM0YLRg9GA0Ysg0KDQvtGB0YHQuNC50YHQutC+0Lkg0KTQtdC00LXRgNCw0YbQuNC4INC+0YIgMjUuMTIuMjAwOCDihJYyNTc=",
            "return_info_eng": "PHA+UmV0dXJuL2NoYW5nZSBvZiB0aWNrZXRzIGlzIHBvc3NpYmxlIGluIGNhc2Ugb2YgY2FuY2VsbGF0aW9uLCBzdWJzdGl0dXRpb24gb3IgdHJhbnNmZXIgb2YgdGhlIGV2ZW50LiBGb3IgcmV0dXJuL2NoYW5nZSBvZiB0aWNrZXRzIGNvbnRhY3QgdG8gTGltaXRlZCBMaWFiaWxpdHkgQ29tcGFueSDigJxLdWx0dXJuYXlhIFNsdXpoYmHigJ0gKHJlZ2lzdGVyZWQgbnVtYmVyIDExMDc3NDYwNjU0MjYsIGFkZHJlc3MgVGFnYW5za2F5IHN0ci4sIDI2LCBidWlsZC4xLCBNb3Njb3csIDEwOTE0NywgdGVsLig0OTUpMjI4LTIwODApLjwvcD4=",
            "return_info_rus": "PHA+0JLQvtC30LLRgNCw0YIg0Lgv0LjQu9C4INC30LDQvNC10L3QsCDQsdC40LvQtdGC0L7QsiDQstC+0LfQvNC+0LbQvdCwINCyINGB0LvRg9GH0LDQtSDQvtGC0LzQtdC90YssINC30LDQvNC10L3RiyDQuNC70Lgg0L/QtdGA0LXQvdC+0YHQsCDQvNC10YDQvtC/0YDQuNGP0YLQuNGPLiDQl9CwINCy0L7Qt9Cy0YDQsNGC0L7QvCDQuC/QuNC70Lgg0LfQsNC80LXQvdC+0Lkg0LHQuNC70LXRgtCwINC+0LHRgNCw0YnQsNGC0YzRgdGPINCyINCe0LHRidC10YHRgtCy0L4g0YEg0L7Qs9GA0LDQvdC40YfQtdC90L3QvtC5INC+0YLQstC10YLRgdGC0LLQtdC90L3QvtGB0YLRjNGOIMKr0JrRg9C70YzRgtGD0YDQvdCw0Y8g0YHQu9GD0LbQsdCwwrsgKNCe0JPQoNCdIDExMDc3NDYwNjU0MjYuINCQ0LTRgNC10YE6IDEwOTE0Nywg0LMuINCc0L7RgdC60LLQsCwg0YPQuy4g0KLQsNCz0LDQvdGB0LrQsNGPLCDQtC4yNiwg0YHRgtGALjEsINGC0LXQuy4gKDQ5NSkyMjgtMjA4MCkuPC9wPg==",
            "to_pdf": false,
            "topline_eng": "This page is considered as a ticket. Valid to the entrance",
            "topline_rus": "Вся страница является билетом. Действителен ко входу"
        },
        "nds_included": false,
        "order": {
            "date": 1421444656378,
            "email": "millir_nika@mail.ru",
            "id": 19413756,
            "is_mine": false,
            "name": "Прусова Вера Валерьевна",
            "payment_method": {
                "code": 7,
                "paid": true,
                "status": "epayment.status.payment_successful",
                "title": "Терминалы QIWI и QIWI-кошелёк"
            },
            "phone": "89055662254",
            "selfget": true,
            "status": 3,
            "typeofpayment": {
                "epayment": true,
                "icon": "/basket/pm_qiwi.png",
                "id": 4,
                "priority": 6,
                "title": "Терминалы QIWI и QIWI-кошелёк"
            },
            "typeofsale": {
                "icon": "/basket/del_eticket.png",
                "id": 4,
                "priority": 10,
                "title": "Eticket"
            }
        },
        "order_id": 19413756,
        "price": 1800,
        "row": 2,
        "seat": 3,
        "sector": {
            "id": 5927,
            "title": "Входной билет"
        },
        "subevent": {
            "age": 16,
            "date": 1428253200000,
            "has_offer": false,
            "id": 462241,
            "title": "Eisbrecher",
            "venue": {
                "address": "Москва, Бумажный пр-д, д. 19/3",
                "eng_title": "",
                "id": 1001,
                "title": "Клуб Volta"
            }
        },
        "supplier": {
            "id": 1290,
            "inn": "7806491445",
            "legal_address": "г.Санкт-Петербург, проспект Энтузиастов, дом 47, корпус1",
            "name": "ООО «Культпродукт»"
        }
    },
    "ts": 1422550381315
}
````
