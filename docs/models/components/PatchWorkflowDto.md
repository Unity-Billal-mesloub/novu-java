# PatchWorkflowDto


## Fields

| Field                                            | Type                                             | Required                                         | Description                                      |
| ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ |
| `active`                                         | *Optional\<Boolean>*                             | :heavy_minus_sign:                               | Activate or deactivate the workflow              |
| `name`                                           | *Optional\<String>*                              | :heavy_minus_sign:                               | New name for the workflow                        |
| `description`                                    | *Optional\<String>*                              | :heavy_minus_sign:                               | Updated description of the workflow              |
| `tags`                                           | List\<*String*>                                  | :heavy_minus_sign:                               | Tags associated with the workflow                |
| `payloadSchema`                                  | Map\<String, *Object*>                           | :heavy_minus_sign:                               | The payload JSON Schema for the workflow         |
| `validatePayload`                                | *Optional\<Boolean>*                             | :heavy_minus_sign:                               | Enable or disable payload schema validation      |
| `isTranslationEnabled`                           | *Optional\<Boolean>*                             | :heavy_minus_sign:                               | Enable or disable translations for this workflow |