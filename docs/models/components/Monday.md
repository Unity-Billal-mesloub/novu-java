# Monday

Monday schedule


## Fields

| Field                                                          | Type                                                           | Required                                                       | Description                                                    | Example                                                        |
| -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- |
| `isEnabled`                                                    | *boolean*                                                      | :heavy_check_mark:                                             | Day schedule enabled                                           | true                                                           |
| `hours`                                                        | List\<[TimeRangeDto](../../models/components/TimeRangeDto.md)> | :heavy_minus_sign:                                             | Hours                                                          | [<br/>{<br/>"start": "09:00 AM",<br/>"end": "05:00 PM"<br/>}<br/>] |