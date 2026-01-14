# SubscribersPreferences

## Overview

### Available Operations

* [bulkUpdate](#bulkupdate) - Bulk update subscriber preferences

## bulkUpdate

Bulk update subscriber preferences by its unique key identifier **subscriberId**. 
    This API allows updating multiple workflow preferences in a single request.

### Example Usage

<!-- UsageSnippet language="java" operationID="SubscribersController_bulkUpdateSubscriberPreferences" method="patch" path="/v2/subscribers/{subscriberId}/preferences/bulk" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.BulkUpdateSubscriberPreferencesDto;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.SubscribersControllerBulkUpdateSubscriberPreferencesResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        SubscribersControllerBulkUpdateSubscriberPreferencesResponse res = sdk.subscribersPreferences().bulkUpdate()
                .subscriberId("<id>")
                .body(BulkUpdateSubscriberPreferencesDto.builder()
                    .preferences(List.of())
                    .build())
                .call();

        if (res.getPreferencesResponseDtos().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                           | Type                                                                                                | Required                                                                                            | Description                                                                                         |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `subscriberId`                                                                                      | *String*                                                                                            | :heavy_check_mark:                                                                                  | N/A                                                                                                 |
| `idempotencyKey`                                                                                    | *Optional\<String>*                                                                                 | :heavy_minus_sign:                                                                                  | A header for idempotency purposes                                                                   |
| `body`                                                                                              | [BulkUpdateSubscriberPreferencesDto](../../models/components/BulkUpdateSubscriberPreferencesDto.md) | :heavy_check_mark:                                                                                  | N/A                                                                                                 |

### Response

**[SubscribersControllerBulkUpdateSubscriberPreferencesResponse](../../models/operations/SubscribersControllerBulkUpdateSubscriberPreferencesResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |