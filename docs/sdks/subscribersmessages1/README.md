# SubscribersMessages

## Overview

### Available Operations

* [updateAsSeen](#updateasseen) - Update notification action status

## updateAsSeen

Update in-app (inbox) notification's action status by its unique key identifier **messageId** and type field **type**. 
      **type** field can be **primary** or **secondary**

### Example Usage

<!-- UsageSnippet language="java" operationID="SubscribersV1Controller_markActionAsSeen" method="post" path="/v1/subscribers/{subscriberId}/messages/{messageId}/actions/{type}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.MarkMessageActionAsSeenDto;
import org.openapis.openapi.models.components.MarkMessageActionAsSeenDtoStatus;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.SubscribersV1ControllerMarkActionAsSeenRequest;
import org.openapis.openapi.models.operations.SubscribersV1ControllerMarkActionAsSeenResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        SubscribersV1ControllerMarkActionAsSeenRequest req = SubscribersV1ControllerMarkActionAsSeenRequest.builder()
                .messageId("<id>")
                .type("<value>")
                .subscriberId("<id>")
                .body(MarkMessageActionAsSeenDto.builder()
                    .status(MarkMessageActionAsSeenDtoStatus.PENDING)
                    .build())
                .build();

        SubscribersV1ControllerMarkActionAsSeenResponse res = sdk.subscribersMessages().updateAsSeen()
                .request(req)
                .call();

        if (res.messageResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                   | Type                                                                                                                        | Required                                                                                                                    | Description                                                                                                                 |
| --------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| `request`                                                                                                                   | [SubscribersV1ControllerMarkActionAsSeenRequest](../../models/operations/SubscribersV1ControllerMarkActionAsSeenRequest.md) | :heavy_check_mark:                                                                                                          | The request object to use for the request.                                                                                  |

### Response

**[SubscribersV1ControllerMarkActionAsSeenResponse](../../models/operations/SubscribersV1ControllerMarkActionAsSeenResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |