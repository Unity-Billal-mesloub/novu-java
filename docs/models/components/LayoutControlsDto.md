# LayoutControlsDto


## Fields

| Field                                                                       | Type                                                                        | Required                                                                    | Description                                                                 |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `dataSchema`                                                                | Map\<String, *Object*>                                                      | :heavy_minus_sign:                                                          | JSON Schema for data                                                        |
| `uiSchema`                                                                  | [Optional\<UiSchema>](../../models/components/UiSchema.md)                  | :heavy_minus_sign:                                                          | UI Schema for rendering                                                     |
| `values`                                                                    | [LayoutControlValuesDto](../../models/components/LayoutControlValuesDto.md) | :heavy_check_mark:                                                          | Email layout controls                                                       |