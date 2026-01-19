# AutoConfigureIntegrationResponseDto


## Fields

| Field                                                              | Type                                                               | Required                                                           | Description                                                        |
| ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| `success`                                                          | *boolean*                                                          | :heavy_check_mark:                                                 | Indicates whether the auto-configuration was successful            |
| `message`                                                          | *Optional\<String>*                                                | :heavy_minus_sign:                                                 | Optional message describing the result or any errors that occurred |
| `integration`                                                      | [Optional\<Integration>](../../models/components/Integration.md)   | :heavy_minus_sign:                                                 | The updated configurations after auto-configuration                |