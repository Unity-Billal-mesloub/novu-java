# SubscribersV1ControllerMarkMessagesAsRequest


## Fields

| Field                                                                         | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `subscriberId`                                                                | *String*                                                                      | :heavy_check_mark:                                                            | N/A                                                                           |
| `idempotencyKey`                                                              | *Optional\<String>*                                                           | :heavy_minus_sign:                                                            | A header for idempotency purposes                                             |
| `body`                                                                        | [MessageMarkAsRequestDto](../../models/components/MessageMarkAsRequestDto.md) | :heavy_check_mark:                                                            | N/A                                                                           |