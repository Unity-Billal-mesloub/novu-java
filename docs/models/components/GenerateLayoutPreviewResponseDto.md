# GenerateLayoutPreviewResponseDto


## Fields

| Field                                                                         | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `previewPayloadExample`                                                       | [LayoutPreviewPayloadDto](../../models/components/LayoutPreviewPayloadDto.md) | :heavy_check_mark:                                                            | Preview payload example                                                       |
| `schema`                                                                      | Map\<String, *Object*>                                                        | :heavy_minus_sign:                                                            | The payload schema that was used to generate the preview payload example      |
| `result`                                                                      | [ResultUnion](../../models/components/ResultUnion.md)                         | :heavy_check_mark:                                                            | Preview result                                                                |