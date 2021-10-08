

 <!-- range HasServices -->






# MarketDataService
Сервис получения биржевой информации:</br> **1**. свечи;</br> **2**. стаканы;</br> **3**. торговые статусы;</br> **4**. лента сделок.

##Методы сервиса


### GetCandles
Метод запроса исторических свечей по инструменту

- Тело запроса — [GetCandlesRequest](#getcandlesrequest)

- Тело ответа — [GetCandlesResponse](#getcandlesresponse)


### GetLastPrices
Метод запроса последних цен по инструментам

- Тело запроса — [GetLastPricesRequest](#getlastpricesrequest)

- Тело ответа — [GetLastPricesResponse](#getlastpricesresponse)


### GetOrderBook
Метод получения стакана по инструменту

- Тело запроса — [GetOrderBookRequest](#getorderbookrequest)

- Тело ответа — [GetOrderBookResponse](#getorderbookresponse)


### GetTradingStatus
Метод запроса статуса торгов по инструментам

- Тело запроса — [GetTradingStatusRequest](#gettradingstatusrequest)

- Тело ответа — [TradingStatus](#tradingstatus)

 <!-- range .Methods -->


# MarketDataStreamService


##Методы сервиса


### MarketDataStream
Двусторонний стрим предоставления биржевой информации

- Тело запроса — [MarketDataRequest](#marketdatarequest)

- Тело ответа — [MarketDataResponse](#marketdataresponse)

 <!-- range .Methods -->
 <!-- range .Services -->

##Сообщения методов



### MarketDataRequest
Запрос подписки или отписки на определённые биржевые данные


| Field | Type | Description |
| ----- | ---- | ----------- |
| subscribe_candles_request |  [SubscribeCandlesRequest](#subscribecandlesrequest) | Запрос подписки на свечи |
| subscribe_order_book_request |  [SubscribeOrderBookRequest](#subscribeorderbookrequest) | Запрос подписки на стаканы |
| subscribe_trades_request |  [SubscribeTradesRequest](#subscribetradesrequest) | Запрос подписки на ленту обезличенных сделок |
| subscribe_info_request |  [SubscribeInfoRequest](#subscribeinforequest) | Запрос подписки на торговые статусы инструментов |
 <!-- end Fields -->
 <!-- end HasFields -->


### MarketDataResponse
Пакет биржевой информации по подписке


| Field | Type | Description |
| ----- | ---- | ----------- |
| subscribe_candles_response |  [SubscribeCandlesResponse](#subscribecandlesresponse) | Результат подписки на свечи |
| subscribe_order_book_response |  [SubscribeOrderBookResponse](#subscribeorderbookresponse) | Результат подписки на стаканы |
| subscribe_trades_response |  [SubscribeTradesResponse](#subscribetradesresponse) | Результат подписки на поток обезличенных сделок |
| subscribe_info_response |  [SubscribeInfoResponse](#subscribeinforesponse) | Результат подписки на торговые статусы инструментов |
| candle |  [Candle](#candle) | Свеча |
| trade |  [Trade](#trade) | Сделки |
| orderbook |  [OrderBook](#orderbook) | Стакан |
| trading_status |  [TradingStatus](#tradingstatus) | Торговый статус |
 <!-- end Fields -->
 <!-- end HasFields -->


### SubscribeCandlesRequest
subscribeCandles | Изменения статуса подписки на свечи


| Field | Type | Description |
| ----- | ---- | ----------- |
| subscription_action |  [SubscriptionAction](#subscriptionaction) | Изменение статуса подписки |
| instruments | Массив объектов [CandleInstrument](#candleinstrument) | Массив инструментов для подписки на свечи |
 <!-- end Fields -->
 <!-- end HasFields -->


### CandleInstrument



| Field | Type | Description |
| ----- | ---- | ----------- |
| figi |  [string](#string) | Figi-идентификатор инструмента |
| interval |  [SubscriptionInterval](#subscriptioninterval) | Интервал свечей |
 <!-- end Fields -->
 <!-- end HasFields -->


### SubscribeCandlesResponse



| Field | Type | Description |
| ----- | ---- | ----------- |
| tracking_id |  [string](#string) | Уникальный идентификатор запроса, подробнее: [tracking_id](https://oridisboss.github.io/doctest/grpc#tracking) |
| candles_subscriptions | Массив объектов [CandleSubscription](#candlesubscription) | Массив статусов подписки на свечи |
 <!-- end Fields -->
 <!-- end HasFields -->


### CandleSubscription



| Field | Type | Description |
| ----- | ---- | ----------- |
| figi |  [string](#string) | Figi-идентификатор инструмента |
| interval |  [SubscriptionInterval](#subscriptioninterval) | Интервал свечей |
| subscription_status |  [SubscriptionStatus](#subscriptionstatus) | Статус подписки |
 <!-- end Fields -->
 <!-- end HasFields -->


### SubscribeOrderBookRequest
subscribeOrderbook | Изменение статуса подписки на стаканы


| Field | Type | Description |
| ----- | ---- | ----------- |
| subscription_action |  [SubscriptionAction](#subscriptionaction) | Изменение статуса подписки |
| instruments | Массив объектов [OrderBookInstrument](#orderbookinstrument) | Массив инструментов для подписки на стаканы |
 <!-- end Fields -->
 <!-- end HasFields -->


### OrderBookInstrument



| Field | Type | Description |
| ----- | ---- | ----------- |
| figi |  [string](#string) | Figi-идентификатор инструмента |
| depth |  [int32](#int32) | Глубина стакана |
 <!-- end Fields -->
 <!-- end HasFields -->


### SubscribeOrderBookResponse



| Field | Type | Description |
| ----- | ---- | ----------- |
| tracking_id |  [string](#string) | Уникальный идентификатор запроса, подробнее: [tracking_id](https://oridisboss.github.io/doctest/grpc#tracking) |
| order_book_subscriptions | Массив объектов [OrderBookSubscription](#orderbooksubscription) | Массив статусов подписки на стаканы |
 <!-- end Fields -->
 <!-- end HasFields -->


### OrderBookSubscription



| Field | Type | Description |
| ----- | ---- | ----------- |
| figi |  [string](#string) | Figi-идентификатор инструмента |
| depth |  [int32](#int32) | Глубина стакана |
| subscription_status |  [SubscriptionStatus](#subscriptionstatus) | Статус подписки |
 <!-- end Fields -->
 <!-- end HasFields -->


### SubscribeTradesRequest
subscribeTrades | Изменение статуса подписки на поток обезличенных сделок


| Field | Type | Description |
| ----- | ---- | ----------- |
| subscription_action |  [SubscriptionAction](#subscriptionaction) | Изменение статуса подписки |
| instruments | Массив объектов [TradeInstrument](#tradeinstrument) | Массив инструментов для подписки на поток обезличенных сделок |
 <!-- end Fields -->
 <!-- end HasFields -->


### TradeInstrument



| Field | Type | Description |
| ----- | ---- | ----------- |
| figi |  [string](#string) | Figi-идентификатор инструмента |
 <!-- end Fields -->
 <!-- end HasFields -->


### SubscribeTradesResponse



| Field | Type | Description |
| ----- | ---- | ----------- |
| tracking_id |  [string](#string) | Уникальный идентификатор запроса, подробнее: [tracking_id](https://oridisboss.github.io/doctest/grpc#tracking) |
| trade_subscriptions | Массив объектов [TradeSubscription](#tradesubscription) | Массив статусов подписки на поток сделок |
 <!-- end Fields -->
 <!-- end HasFields -->


### TradeSubscription



| Field | Type | Description |
| ----- | ---- | ----------- |
| figi |  [string](#string) | Figi-идентификатор инструмента |
| subscription_status |  [SubscriptionStatus](#subscriptionstatus) | Статус подписки |
 <!-- end Fields -->
 <!-- end HasFields -->


### SubscribeInfoRequest
subscribeInfo | Изменение статуса подписки на торговый статус инструмента


| Field | Type | Description |
| ----- | ---- | ----------- |
| subscription_action |  [SubscriptionAction](#subscriptionaction) | Изменение статуса подписки |
| instruments | Массив объектов [InfoInstrument](#infoinstrument) | Массив инструментов для подписки на торговый статус |
 <!-- end Fields -->
 <!-- end HasFields -->


### InfoInstrument



| Field | Type | Description |
| ----- | ---- | ----------- |
| figi |  [string](#string) | Figi-идентификатор инструмента |
 <!-- end Fields -->
 <!-- end HasFields -->


### SubscribeInfoResponse



| Field | Type | Description |
| ----- | ---- | ----------- |
| tracking_id |  [string](#string) | Уникальный идентификатор запроса, подробнее: [tracking_id](https://oridisboss.github.io/doctest/grpc#tracking) |
| info_subscriptions | Массив объектов [InfoSubscription](#infosubscription) | Массив статусов подписки на торговый статус |
 <!-- end Fields -->
 <!-- end HasFields -->


### InfoSubscription



| Field | Type | Description |
| ----- | ---- | ----------- |
| figi |  [string](#string) | Figi-идентификатор инструмента |
| subscription_status |  [SubscriptionStatus](#subscriptionstatus) | Статус подписки |
 <!-- end Fields -->
 <!-- end HasFields -->


### Candle
Выходные параметры. Пакет Candles


| Field | Type | Description |
| ----- | ---- | ----------- |
| figi |  [string](#string) | Figi-идентификатор инструмента |
| interval |  [SubscriptionInterval](#subscriptioninterval) | Интервал свечи |
| open |  [Quotation](#quotation) | Цена открытия за 1 лот |
| high |  [Quotation](#quotation) | Максимальная цена за 1 лот |
| low |  [Quotation](#quotation) | Минимальная цена за 1 лот |
| close |  [Quotation](#quotation) | Цена закрытия за 1 лот |
| value |  [int64](#int64) | Объём сделок в лотах |
| time |  [google.protobuf.Timestamp](#googleprotobuftimestamp) | Время свечи в часовом поясе UTC |
 <!-- end Fields -->
 <!-- end HasFields -->


### OrderBook



| Field | Type | Description |
| ----- | ---- | ----------- |
| figi |  [string](#string) | Figi-идентификатор инструмента |
| depth |  [int32](#int32) | Глубина стакана |
| is_consistent |  [bool](#bool) | Флаг консистентности стакана. **false** значит не все заявки попали в стакан по причинам сетевых задержек или нарушения порядка доставки. |
| bids | Массив объектов [Order](#order) | Массив предложений |
| asks | Массив объектов [Order](#order) | Массив спроса |
 <!-- end Fields -->
 <!-- end HasFields -->


### Order



| Field | Type | Description |
| ----- | ---- | ----------- |
| price |  [Quotation](#quotation) | Цена за 1 лот |
| quantity |  [int64](#int64) | Количество в лотах |
 <!-- end Fields -->
 <!-- end HasFields -->


### Trade



| Field | Type | Description |
| ----- | ---- | ----------- |
| figi |  [string](#string) | Figi-идентификатор инструмента |
| direction |  [TradeDirection](#tradedirection) | Направление сделки |
| price |  [Quotation](#quotation) | Цена за 1 лот |
| quantity |  [int64](#int64) | Количество лотов |
| timestamp |  [google.protobuf.Timestamp](#googleprotobuftimestamp) | Время сделки в часовом поясе UTC по времени биржи |
 <!-- end Fields -->
 <!-- end HasFields -->


### TradingStatus



| Field | Type | Description |
| ----- | ---- | ----------- |
| figi |  [string](#string) | Figi-идентификатор инструмента |
| trading_status |  [SecurityTradingStatus](#securitytradingstatus) | Статус торговли инструментом |
 <!-- end Fields -->
 <!-- end HasFields -->


### GetCandlesRequest



| Field | Type | Description |
| ----- | ---- | ----------- |
| figi |  [string](#string) | Figi-идентификатор инструмента |
| from |  [google.protobuf.Timestamp](#googleprotobuftimestamp) | Начало запрашиваемого периода в часовом поясе UTC |
| to |  [google.protobuf.Timestamp](#googleprotobuftimestamp) | Окончание запрашиваемого периода в часовом поясе UTC |
| interval |  [CandleInterval](#candleinterval) | Интервал запрошенных свечей |
 <!-- end Fields -->
 <!-- end HasFields -->


### GetCandlesResponse



| Field | Type | Description |
| ----- | ---- | ----------- |
| candles | Массив объектов [HistoricCandle](#historiccandle) | Массив свечей |
 <!-- end Fields -->
 <!-- end HasFields -->


### HistoricCandle



| Field | Type | Description |
| ----- | ---- | ----------- |
| open |  [Quotation](#quotation) | Цена открытия за 1 лот |
| high |  [Quotation](#quotation) | Максимальная цена за 1 лот |
| low |  [Quotation](#quotation) | Минимальная цена за 1 лот |
| close |  [Quotation](#quotation) | Цена закрытия за 1 лот |
| volume |  [int64](#int64) | Объём торгов в лотах |
| time |  [google.protobuf.Timestamp](#googleprotobuftimestamp) | Время свечи в часовом поясе UTC |
| is_complete |  [bool](#bool) | Признак завершённости свечи. **false** значит, свеча за текущие интервал ещё сформирована не полностью |
 <!-- end Fields -->
 <!-- end HasFields -->


### GetLastPricesRequest



| Field | Type | Description |
| ----- | ---- | ----------- |
| figi | Массив объектов [string](#string) | Массив figi-идентификаторов инструментов |
 <!-- end Fields -->
 <!-- end HasFields -->


### GetLastPricesResponse



| Field | Type | Description |
| ----- | ---- | ----------- |
| last_prices | Массив объектов [LastPrice](#lastprice) | Массив последних цен |
 <!-- end Fields -->
 <!-- end HasFields -->


### LastPrice



| Field | Type | Description |
| ----- | ---- | ----------- |
| figi |  [string](#string) | Идентификатор инструмента |
| price |  [MoneyValue](#moneyvalue) | Последняя цена за 1 лот |
| time |  [google.protobuf.Timestamp](#googleprotobuftimestamp) | Время получения последней цены в часовом поясе UTC по времени биржи |
 <!-- end Fields -->
 <!-- end HasFields -->


### GetOrderBookRequest



| Field | Type | Description |
| ----- | ---- | ----------- |
| figi |  [string](#string) | Figi-идентификатор инструмента |
| depth |  [int32](#int32) | Глубина стакана |
 <!-- end Fields -->
 <!-- end HasFields -->


### GetOrderBookResponse



| Field | Type | Description |
| ----- | ---- | ----------- |
| figi |  [string](#string) | Figi-идентификатор инструмента |
| depth |  [int32](#int32) | Глубина стакана |
| bids | Массив объектов [Order](#order) | Множество пар значений на покупку |
| asks | Массив объектов [Order](#order) | Множество пар значений на продажу |
 <!-- end Fields -->
 <!-- end HasFields -->


### GetTradingStatusRequest



| Field | Type | Description |
| ----- | ---- | ----------- |
| figi |  [string](#string) | Идентификатор инструмента |
 <!-- end Fields -->
 <!-- end HasFields -->
 <!-- end messages -->

## Enums


### SubscriptionAction


| Name | Number | Description |
| ---- | ------ | ----------- |
| SUBSCRIPTION_ACTION_UNSPECIFIED | 0 | Статус подписки не определён |
| SUBSCRIPTION_ACTION_SUBSCRIBE | 1 | Подписаться |
| SUBSCRIPTION_ACTION_UNSUBSCRIBE | 2 | Отписаться |




### SubscriptionInterval


| Name | Number | Description |
| ---- | ------ | ----------- |
| SUBSCRIPTION_INTERVAL_UNSPECIFIED | 0 | Интервал свечи не определён |
| SUBSCRIPTION_INTERVAL_ONE_MINUTE | 1 | Минутные свечи |
| SUBSCRIPTION_INTERVAL_FIVE_MINUTES | 2 | Пятиминутные свечи |




### SubscriptionStatus


| Name | Number | Description |
| ---- | ------ | ----------- |
| SUBSCRIPTION_STATUS_UNSPECIFIED | 0 | Статус подписки не определён |
| SUBSCRIPTION_STATUS_SUCCESS | 1 | Успешно |
| SUBSCRIPTION_STATUS_INSTRUMENT_NOT_FOUND | 2 | Инструмент не найден |
| SUBSCRIPTION_STATUS_SUBSCRIPTION_STATUS_IS_INVALID | 3 | Некорректный статус подписки, список возможных значений: [SubscriptionAction](/doctest/marketdata#subscriptionaction) |
| SUBSCRIPTION_STATUS_DEPTH_IS_INVALID | 4 | Некорректная глубина стакана, требуется указать целое число от 1 до 50 |
| SUBSCRIPTION_STATUS_INTERVAL_IS_INVALID | 5 | Некорректный интервал свечей, список возможных значений: [SubscriptionInterval](/doctest/marketdata#subscriptioninterval) |
| SUBSCRIPTION_STATUS_LIMIT_IS_EXCEEDED | 6 | Превышен лимит подписок в рамках стрима, подробнее: [Лимитная политика](/doctest/limits/) |
| SUBSCRIPTION_STATUS_INTERNAL_ERROR | 7 | Внутренняя ошибка сервиса |




### TradeDirection


| Name | Number | Description |
| ---- | ------ | ----------- |
| TRADE_DIRECTION_UNSPECIFIED | 0 | Направление сделки не определено |
| TRADE_DIRECTION_BUY | 1 | Покупка |
| TRADE_DIRECTION_SELL | 2 | Продажа |




### CandleInterval


| Name | Number | Description |
| ---- | ------ | ----------- |
| CANDLE_INTERVAL_UNSPECIFIED | 0 | Интервал не определён |
| CANDLE_INTERVAL_1_MIN | 1 | 1 минута |
| CANDLE_INTERVAL_5_MIN | 2 | 5 минут |
| CANDLE_INTERVAL_15_MIN | 3 | 15 минут |
| CANDLE_INTERVAL_HOUR | 4 | 1 час |
| CANDLE_INTERVAL_DAY | 5 | 1 день |


 <!-- range .Enums -->
 <!-- range HasServices -->
 <!-- range .Files -->

## Нестандартные типы данных

### MoneyValue
Денежная сумма в определенной валюте

| Field | Type | Description |
| ----- | ---- | ----------- |
| currency |  [string](#string) | Строковый ISO-код валюты |
| units |  [int64](#int64) | Целая часть суммы, может быть отрицательным числом |
| nano |  [int32](#int32) | Дробная часть суммы, может быть отрицательным числом |


### Quotation
Котировка - денежная сумма без указания валюты

| Field | Type | Description |
| ----- | ---- | ----------- |
| units |  [int64](#int64) | Целая часть суммы, может быть отрицательным числом |
| nano |  [int32](#int32) | Дробная часть суммы, может быть отрицательным числом |
