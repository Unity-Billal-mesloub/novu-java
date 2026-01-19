# LayoutsControllerUpdateRequest


## Fields

| Field                                                         | Type                                                          | Required                                                      | Description                                                   |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| `layoutId`                                                    | *String*                                                      | :heavy_check_mark:                                            | N/A                                                           |
| `idempotencyKey`                                              | *Optional\<String>*                                           | :heavy_minus_sign:                                            | A header for idempotency purposes                             |
| `body`                                                        | [UpdateLayoutDto](../../models/components/UpdateLayoutDto.md) | :heavy_check_mark:                                            | Layout update details                                         |