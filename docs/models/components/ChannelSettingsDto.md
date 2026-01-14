# ChannelSettingsDto


## Fields

| Field                                                                       | Type                                                                        | Required                                                                    | Description                                                                 |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `providerId`                                                                | [ChatOrPushProviderEnum](../../models/components/ChatOrPushProviderEnum.md) | :heavy_check_mark:                                                          | The provider identifier for the credentials                                 |
| `integrationIdentifier`                                                     | *Optional\<String>*                                                         | :heavy_minus_sign:                                                          | The integration identifier                                                  |
| `credentials`                                                               | [ChannelCredentials](../../models/components/ChannelCredentials.md)         | :heavy_check_mark:                                                          | Credentials payload for the specified provider                              |
| `integrationId`                                                             | *String*                                                                    | :heavy_check_mark:                                                          | The unique identifier of the integration associated with this channel.      |