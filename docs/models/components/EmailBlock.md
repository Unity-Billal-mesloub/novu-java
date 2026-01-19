# EmailBlock


## Fields

| Field                                                                      | Type                                                                       | Required                                                                   | Description                                                                |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `type`                                                                     | [EmailBlockTypeEnum](../../models/components/EmailBlockTypeEnum.md)        | :heavy_check_mark:                                                         | Type of the email block                                                    |
| `content`                                                                  | *String*                                                                   | :heavy_check_mark:                                                         | Content of the email block                                                 |
| `url`                                                                      | *Optional\<String>*                                                        | :heavy_minus_sign:                                                         | URL associated with the email block, if any                                |
| `styles`                                                                   | [Optional\<EmailBlockStyles>](../../models/components/EmailBlockStyles.md) | :heavy_minus_sign:                                                         | Styles applied to the email block                                          |