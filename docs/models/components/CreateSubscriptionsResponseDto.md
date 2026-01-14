# CreateSubscriptionsResponseDto


## Fields

| Field                                                                                | Type                                                                                 | Required                                                                             | Description                                                                          |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| `data`                                                                               | List\<[SubscriptionResponseDto](../../models/components/SubscriptionResponseDto.md)> | :heavy_check_mark:                                                                   | The list of successfully created subscriptions                                       |
| `meta`                                                                               | [MetaDto](../../models/components/MetaDto.md)                                        | :heavy_check_mark:                                                                   | Metadata about the operation                                                         |
| `errors`                                                                             | List\<[SubscriptionErrorDto](../../models/components/SubscriptionErrorDto.md)>       | :heavy_minus_sign:                                                                   | The list of errors for failed subscription attempts                                  |