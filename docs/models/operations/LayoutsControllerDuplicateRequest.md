# LayoutsControllerDuplicateRequest


## Fields

| Field                                                               | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `layoutId`                                                          | *String*                                                            | :heavy_check_mark:                                                  | N/A                                                                 |
| `idempotencyKey`                                                    | *Optional\<String>*                                                 | :heavy_minus_sign:                                                  | A header for idempotency purposes                                   |
| `body`                                                              | [DuplicateLayoutDto](../../models/components/DuplicateLayoutDto.md) | :heavy_check_mark:                                                  | N/A                                                                 |