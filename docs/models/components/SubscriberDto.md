# SubscriberDto


## Fields

| Field                                     | Type                                      | Required                                  | Description                               | Example                                   |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| `id`                                      | *String*                                  | :heavy_check_mark:                        | The identifier of the subscriber          | 64da692e9a94fb2e6449ad07                  |
| `subscriberId`                            | *String*                                  | :heavy_check_mark:                        | The external identifier of the subscriber | user-123                                  |
| `avatar`                                  | *JsonNullable\<String>*                   | :heavy_minus_sign:                        | The avatar URL of the subscriber          | https://example.com/avatar.png            |
| `firstName`                               | *JsonNullable\<String>*                   | :heavy_minus_sign:                        | The first name of the subscriber          | John                                      |
| `lastName`                                | *JsonNullable\<String>*                   | :heavy_minus_sign:                        | The last name of the subscriber           | Doe                                       |
| `email`                                   | *JsonNullable\<String>*                   | :heavy_minus_sign:                        | The email of the subscriber               | john@example.com                          |