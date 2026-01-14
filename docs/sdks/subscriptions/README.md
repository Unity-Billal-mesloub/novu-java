# Topics.Subscriptions

## Overview

### Available Operations

* [fetchSubscription](#fetchsubscription) - Get a topic subscription

## fetchSubscription

Get a subscription by its unique identifier for a topic.

### Example Usage

<!-- UsageSnippet language="java" operationID="TopicsController_getTopicSubscription" method="get" path="/v2/topics/{topicKey}/subscriptions/{identifier}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.TopicsControllerGetTopicSubscriptionResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        TopicsControllerGetTopicSubscriptionResponse res = sdk.topics().subscriptions().fetchSubscription()
                .topicKey("<value>")
                .identifier("<value>")
                .call();

        if (res.subscriptionResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                 | Type                                      | Required                                  | Description                               |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| `topicKey`                                | *String*                                  | :heavy_check_mark:                        | The key identifier of the topic           |
| `identifier`                              | *String*                                  | :heavy_check_mark:                        | The unique identifier of the subscription |
| `idempotencyKey`                          | *Optional\<String>*                       | :heavy_minus_sign:                        | A header for idempotency purposes         |

### Response

**[TopicsControllerGetTopicSubscriptionResponse](../../models/operations/TopicsControllerGetTopicSubscriptionResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |