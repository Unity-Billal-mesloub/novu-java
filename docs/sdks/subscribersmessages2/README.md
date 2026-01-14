# Subscribers.Messages

## Overview

### Available Operations

* [markAll](#markall) - Update all notifications state

## markAll

Update all subscriber in-app (inbox) notifications state such as read, unread, seen or unseen by **subscriberId**.

### Example Usage

<!-- UsageSnippet language="java" operationID="SubscribersV1Controller_markAllUnreadAsRead" method="post" path="/v1/subscribers/{subscriberId}/messages/mark-all" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.MarkAllMessageAsRequestDto;
import org.openapis.openapi.models.components.MarkAllMessageAsRequestDtoMarkAs;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.SubscribersV1ControllerMarkAllUnreadAsReadResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        SubscribersV1ControllerMarkAllUnreadAsReadResponse res = sdk.subscribers().messages().markAll()
                .subscriberId("<id>")
                .body(MarkAllMessageAsRequestDto.builder()
                    .markAs(MarkAllMessageAsRequestDtoMarkAs.READ)
                    .build())
                .call();

        if (res.number().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                           | Type                                                                                | Required                                                                            | Description                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `subscriberId`                                                                      | *String*                                                                            | :heavy_check_mark:                                                                  | N/A                                                                                 |
| `idempotencyKey`                                                                    | *Optional\<String>*                                                                 | :heavy_minus_sign:                                                                  | A header for idempotency purposes                                                   |
| `body`                                                                              | [MarkAllMessageAsRequestDto](../../models/components/MarkAllMessageAsRequestDto.md) | :heavy_check_mark:                                                                  | N/A                                                                                 |

### Response

**[SubscribersV1ControllerMarkAllUnreadAsReadResponse](../../models/operations/SubscribersV1ControllerMarkAllUnreadAsReadResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |