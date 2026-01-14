# TopicsControllerUpdateTopicRequest


## Fields

| Field                                                                     | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `topicKey`                                                                | *String*                                                                  | :heavy_check_mark:                                                        | The key identifier of the topic                                           |
| `idempotencyKey`                                                          | *Optional\<String>*                                                       | :heavy_minus_sign:                                                        | A header for idempotency purposes                                         |
| `body`                                                                    | [UpdateTopicRequestDto](../../models/components/UpdateTopicRequestDto.md) | :heavy_check_mark:                                                        | N/A                                                                       |