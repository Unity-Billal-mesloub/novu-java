# TopicsControllerGetTopicSubscriptionRequest


## Fields

| Field                                     | Type                                      | Required                                  | Description                               |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| `topicKey`                                | *String*                                  | :heavy_check_mark:                        | The key identifier of the topic           |
| `identifier`                              | *String*                                  | :heavy_check_mark:                        | The unique identifier of the subscription |
| `idempotencyKey`                          | *Optional\<String>*                       | :heavy_minus_sign:                        | A header for idempotency purposes         |