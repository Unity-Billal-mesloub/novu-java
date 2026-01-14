# TopicPayloadDto


## Fields

| Field                                                                             | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `topicKey`                                                                        | *String*                                                                          | :heavy_check_mark:                                                                | N/A                                                                               |
| `type`                                                                            | [TriggerRecipientsTypeEnum](../../models/components/TriggerRecipientsTypeEnum.md) | :heavy_check_mark:                                                                | N/A                                                                               |
| `exclude`                                                                         | List\<*String*>                                                                   | :heavy_minus_sign:                                                                | Optional array of subscriber IDs to exclude from the topic trigger                |