# SubscribersV1ControllerGetUnseenCountRequest


## Fields

| Field                                          | Type                                           | Required                                       | Description                                    |
| ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- |
| `subscriberId`                                 | *String*                                       | :heavy_check_mark:                             | N/A                                            |
| `seen`                                         | *Optional\<Boolean>*                           | :heavy_minus_sign:                             | Indicates whether to count seen notifications. |
| `limit`                                        | *Optional\<Double>*                            | :heavy_minus_sign:                             | The maximum number of notifications to return. |
| `idempotencyKey`                               | *Optional\<String>*                            | :heavy_minus_sign:                             | A header for idempotency purposes              |