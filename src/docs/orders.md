

 <!-- range HasServices -->






# OrdersService
Сервис предназначен для работы с торговыми поручениями:</br> **1**.
выставление;</br> **2**. отмена;</br> **3**. получение статуса;</br> **4**.
расчёт полной стоимости;</br> **5**. получение списка заявок.

##Методы сервиса


### OrdersStream
Bidirectional stream работы со сделками

- Тело запроса — [OrdersStreamRequest](#ordersstreamrequest)

- Тело ответа — [OrdersStreamResponse](#ordersstreamresponse)


### PostOrder
Метод выставления заявки.

- Тело запроса — [PostOrderRequest](#postorderrequest)

- Тело ответа — [PostOrderResponse](#postorderresponse)


### CancelOrder
Метод отмены биржевой заявки.

- Тело запроса — [CancelOrderRequest](#cancelorderrequest)

- Тело ответа — [CancelOrderResponse](#cancelorderresponse)


### GetOrderState
Метод получения статуса торгового поручения.

- Тело запроса — [GetOrderStateRequest](#getorderstaterequest)

- Тело ответа — [OrderState](#orderstate)


### GetAmountRaw
Метод расчёта полной стоимости заявки.

- Тело запроса — [GetAmountRawRequest](#getamountrawrequest)

- Тело ответа — [GetAmountRawResponse](#getamountrawresponse)


### GetOrders
Метод получения списка активных заявок по счёту.

- Тело запроса — [GetOrdersRequest](#getordersrequest)

- Тело ответа — [GetOrdersResponse](#getordersresponse)

 <!-- range .Methods -->
 <!-- range .Services -->

##Сообщения методов



### OrdersStreamRequest



| Field | Type | Description |
| ----- | ---- | ----------- |
| order_execute |  [PostOrderRequest](#postorderrequest) | Объект выставления заявки. |
| order_cancel |  [CancelOrderRequest](#cancelorderrequest) | Объект отмены заявки. |
| order_state |  [GetOrderStateRequest](#getorderstaterequest) | Объект получения статуса заявки. |
 <!-- end Fields -->
 <!-- end HasFields -->


### OrdersStreamResponse



| Field | Type | Description |
| ----- | ---- | ----------- |
| order_execute |  [PostOrderResponse](#postorderresponse) | Объект ответа выставления заявки. |
| order_cancel |  [CancelOrderResponse](#cancelorderresponse) | Объект ответа отмены заявки. |
| order_state |  [OrderState](#orderstate) | Объект ответа получения статуса заявки. |
 <!-- end Fields -->
 <!-- end HasFields -->


### PostOrderRequest



| Field | Type | Description |
| ----- | ---- | ----------- |
| figi |  [string](#string) | Figi-идентификатор инструмента. |
| quantity |  [int32](#int32) | Количество лотов. |
| price |  [MoneyValue](#moneyvalue) | Цена лота. |
| direction |  [OrderDirection](#orderdirection) | Направление операции. |
| accountId |  [string](#string) | Номер счёта. |
| order_type |  [OrderType](#ordertype) | Тип заявки. |
 <!-- end Fields -->
 <!-- end HasFields -->


### PostOrderResponse



| Field | Type | Description |
| ----- | ---- | ----------- |
| order_id |  [string](#string) | Идентификатор заявки. |
| execution_report_status |  [OrderExecutionReportStatus](#orderexecutionreportstatus) | Текущий статус заявки. |
| lots_requested |  [int32](#int32) | Запрошено лотов. |
| lots_executed |  [int32](#int32) | Исполнено лотов. |
| initial_order_price |  [MoneyValue](#moneyvalue) | Начальная цена заявки. Произведение количества запрошенных лотов на цену. |
| executed_order_price |  [MoneyValue](#moneyvalue) | Исполненная цена заявки. Произведение средней цены покупки на количество лотов. |
| total_order_amount |  [MoneyValue](#moneyvalue) | Итоговая стоимость заявки, включающая все комиссии. |
| initial_commission |  [MoneyValue](#moneyvalue) | Начальная комиссия. Комиссия рассчитанная при выставлении заявки. |
| executed_commission |  [MoneyValue](#moneyvalue) | Фактическая комиссия по итогам исполнения заявки. |
| aci_value |  [MoneyValue](#moneyvalue) | Значение НКД (накопленного купонного дохода) на дату. Подробнее: [НКД при выставлении торговых поручений](/doctest/head-orders#coupon) |
| figi |  [string](#string) | Figi-идентификатор инструмента. |
| direction |  [OrderDirection](#orderdirection) | Направление сделки. |
| initial_security_price |  [MoneyValue](#moneyvalue) | Начальная цена инструмента заявки. |
| order_type |  [OrderType](#ordertype) | Тип заявки. |
| message |  [string](#string) | Дополнительные данные об исполнении заявки. |
 <!-- end Fields -->
 <!-- end HasFields -->


### CancelOrderRequest



| Field | Type | Description |
| ----- | ---- | ----------- |
| account_id |  [string](#string) | Номер счёта. |
| order_id |  [string](#string) | Идентификатор заявки. |
 <!-- end Fields -->
 <!-- end HasFields -->


### CancelOrderResponse



| Field | Type | Description |
| ----- | ---- | ----------- |
| time |  [google.protobuf.Timestamp](#googleprotobuftimestamp) | Дата и время отмены заявки в часовом поясе UTC. |
 <!-- end Fields -->
 <!-- end HasFields -->


### GetOrderStateRequest



| Field | Type | Description |
| ----- | ---- | ----------- |
| account_id |  [string](#string) | Номер счёта. |
| order_id |  [string](#string) | Идентификатор заявки. |
 <!-- end Fields -->
 <!-- end HasFields -->


### GetAmountRawRequest



| Field | Type | Description |
| ----- | ---- | ----------- |
| figi |  [string](#string) | Figi-идентификатор инструмента. |
| quantity |  [float](#float) | Количество лотов. |
| price |  [MoneyValue](#moneyvalue) | Цена лота. |
| direction |  [OrderDirection](#orderdirection) | Направление операции. |
| account_id |  [string](#string) | Номер счёта. |
 <!-- end Fields -->
 <!-- end HasFields -->


### GetAmountRawResponse



| Field | Type | Description |
| ----- | ---- | ----------- |
| commission |  [MoneyValue](#moneyvalue) | Общий размер комиссии. |
| raw_amount |  [MoneyValue](#moneyvalue) | Стоимость заявки. |
| service_commission |  [MoneyValue](#moneyvalue) | Размер сервисной комиссии. |
| aci_value |  [MoneyValue](#moneyvalue) | Значение НКД (накопленного купонного дохода) на дату. Подробнее: [НКД при выставлении торговых поручений](/doctest/head-orders#coupon) |
 <!-- end Fields -->
 <!-- end HasFields -->


### GetOrdersRequest



| Field | Type | Description |
| ----- | ---- | ----------- |
| account_id |  [string](#string) | Номер счёта. |
 <!-- end Fields -->
 <!-- end HasFields -->


### GetOrdersResponse



| Field | Type | Description |
| ----- | ---- | ----------- |
| orders | Массив объектов [OrderState](#orderstate) | Массив активных заявок. |
 <!-- end Fields -->
 <!-- end HasFields -->


### OrderState



| Field | Type | Description |
| ----- | ---- | ----------- |
| order_id |  [string](#string) | Идентификатор заявки. |
| execution_report_status |  [OrderExecutionReportStatus](#orderexecutionreportstatus) | Текущий статус заявки. |
| lots_requested |  [float](#float) | Запрошено лотов. |
| lots_executed |  [float](#float) | Исполнено лотов. |
| initial_order_price |  [MoneyValue](#moneyvalue) | Начальная цена заявки. Произведение количества запрошенных лотов на цену. |
| executed_order_price |  [MoneyValue](#moneyvalue) | Исполненная цена заявки. Произведение средней цены покупки на количество лотов. |
| total_order_amount |  [MoneyValue](#moneyvalue) | Итоговая стоимость заявки, включающая все комиссии. |
| average_position_price |  [MoneyValue](#moneyvalue) | Средняя цена позиции по сделке. |
| initial_commission |  [MoneyValue](#moneyvalue) | Начальная комиссия. Комиссия, рассчитанная на момент подачи заявки. |
| executed_commission |  [MoneyValue](#moneyvalue) | Фактическая комиссия по итогам исполнения заявки. |
| figi |  [string](#string) | Figi-идентификатор инструмента. |
| direction |  [OrderDirection](#orderdirection) | Направление заявки. |
| initial_security_price |  [MoneyValue](#moneyvalue) | Начальная цена инструмента. Цена инструмента на момент выставления заявки. |
| stages | Массив объектов [OrderStage](#orderstage) | Стадии выполнения заявки. |
| service_commission |  [MoneyValue](#moneyvalue) | Сервисная комиссия. |
| currency |  [string](#string) | Валюта заявки. |
| commission_currency |  [string](#string) | Валюта комиссии. |
| order_type |  [OrderType](#ordertype) | Тип заявки. |
| order_date |  [google.protobuf.Timestamp](#googleprotobuftimestamp) | Дата и время выставления заявки в часовом поясе UTC. |
 <!-- end Fields -->
 <!-- end HasFields -->


### OrderStage



| Field | Type | Description |
| ----- | ---- | ----------- |
| price |  [MoneyValue](#moneyvalue) | Цена. |
| quantity |  [float](#float) | Количество лотов. |
| trade_id |  [string](#string) | Идентификатор торговой операции. |
 <!-- end Fields -->
 <!-- end HasFields -->
 <!-- end messages -->

## Enums


### OrderDirection
Направление операции

| Name | Number | Description |
| ---- | ------ | ----------- |
| ORDER_DIRECTION_UNSPECIFIED | 0 | Значение не указано |
| ORDER_DIRECTION_BUY | 1 | Покупка |
| ORDER_DIRECTION_SELL | 2 | Продажа |




### OrderType
Тип заявки

| Name | Number | Description |
| ---- | ------ | ----------- |
| ORDER_TYPE_UNSPECIFIED | 0 | Значение не указано |
| ORDER_TYPE_LIMIT | 1 | Лимитная |
| ORDER_TYPE_MARKET | 2 | Рыночная |




### OrderExecutionReportStatus
Текущий статус заявки (поручения)

| Name | Number | Description |
| ---- | ------ | ----------- |
| EXECUTION_REPORT_STATUS_UNSPECIFIED | 0 | none |
| EXECUTION_REPORT_STATUS_FILL | 1 | Исполнена |
| EXECUTION_REPORT_STATUS_REJECTED | 2 | Отклонена |
| EXECUTION_REPORT_STATUS_CANCELLED | 3 | Отменена пользователем |
| EXECUTION_REPORT_STATUS_NEW | 4 | Новая |
| EXECUTION_REPORT_STATUS_PARTIALLYFILL | 5 | Частично исполнена |


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
