# BulkCreateSubscriberResponseDto


## Fields

| Field                                                                          | Type                                                                           | Required                                                                       | Description                                                                    |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `updated`                                                                      | List\<[UpdatedSubscriberDto](../../models/components/UpdatedSubscriberDto.md)> | :heavy_check_mark:                                                             | An array of subscribers that were successfully updated.                        |
| `created`                                                                      | List\<[CreatedSubscriberDto](../../models/components/CreatedSubscriberDto.md)> | :heavy_check_mark:                                                             | An array of subscribers that were successfully created.                        |
| `failed`                                                                       | List\<[FailedOperationDto](../../models/components/FailedOperationDto.md)>     | :heavy_check_mark:                                                             | An array of failed operations with error messages and optional subscriber IDs. |