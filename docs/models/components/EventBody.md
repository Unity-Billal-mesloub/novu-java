# EventBody


## Fields

| Field                                                         | Type                                                          | Required                                                      | Description                                                   |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| `status`                                                      | [EventBodyStatus](../../models/components/EventBodyStatus.md) | :heavy_check_mark:                                            | Status of the event                                           |
| `date`                                                        | *String*                                                      | :heavy_check_mark:                                            | Date of the event                                             |
| `externalId`                                                  | *Optional\<String>*                                           | :heavy_minus_sign:                                            | External ID from the provider                                 |
| `attempts`                                                    | *Optional\<Double>*                                           | :heavy_minus_sign:                                            | Number of attempts                                            |
| `response`                                                    | *Optional\<String>*                                           | :heavy_minus_sign:                                            | Response from the provider                                    |
| `row`                                                         | *Optional\<String>*                                           | :heavy_minus_sign:                                            | Raw content from the provider webhook                         |