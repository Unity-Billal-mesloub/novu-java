# Topics.Subscribers

## Overview

### Available Operations

* [get](#get) - Check topic subscriber

## get

Check if a subscriber belongs to a certain topic

### Example Usage

<!-- UsageSnippet language="java" operationID="TopicsV1Controller_getTopicSubscriber" method="get" path="/v1/topics/{topicKey}/subscribers/{externalSubscriberId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.TopicsV1ControllerGetTopicSubscriberResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        TopicsV1ControllerGetTopicSubscriberResponse res = sdk.topics().subscribers().get()
                .externalSubscriberId("<id>")
                .topicKey("<value>")
                .call();

        if (res.topicSubscriberDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                         | Type                              | Required                          | Description                       |
| --------------------------------- | --------------------------------- | --------------------------------- | --------------------------------- |
| `externalSubscriberId`            | *String*                          | :heavy_check_mark:                | The external subscriber id        |
| `topicKey`                        | *String*                          | :heavy_check_mark:                | The topic key                     |
| `idempotencyKey`                  | *Optional\<String>*               | :heavy_minus_sign:                | A header for idempotency purposes |

### Response

**[TopicsV1ControllerGetTopicSubscriberResponse](../../models/operations/TopicsV1ControllerGetTopicSubscriberResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |