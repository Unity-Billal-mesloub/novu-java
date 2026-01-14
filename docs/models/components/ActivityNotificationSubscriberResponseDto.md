# ActivityNotificationSubscriberResponseDto


## Fields

| Field                                                | Type                                                 | Required                                             | Description                                          |
| ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- |
| `firstName`                                          | *Optional\<String>*                                  | :heavy_minus_sign:                                   | First name of the subscriber                         |
| `subscriberId`                                       | *String*                                             | :heavy_check_mark:                                   | External unique identifier of the subscriber         |
| `id`                                                 | *String*                                             | :heavy_check_mark:                                   | Internal to Novu unique identifier of the subscriber |
| `lastName`                                           | *Optional\<String>*                                  | :heavy_minus_sign:                                   | Last name of the subscriber                          |
| `email`                                              | *Optional\<String>*                                  | :heavy_minus_sign:                                   | Email address of the subscriber                      |
| `phone`                                              | *Optional\<String>*                                  | :heavy_minus_sign:                                   | Phone number of the subscriber                       |