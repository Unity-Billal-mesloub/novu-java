# Subscribers.Preferences

## Overview

### Available Operations

* [getPreferences](#getpreferences) - Retrieve subscriber preferences

## getPreferences

Retrieve subscriber channel preferences by its unique key identifier **subscriberId**. 
    This API returns all five channels preferences for all workflows and global preferences.

### Example Usage

<!-- UsageSnippet language="java" operationID="SubscribersController_getSubscriberPreferences" method="get" path="/v2/subscribers/{subscriberId}/preferences" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.Criticality;
import org.openapis.openapi.models.operations.SubscribersControllerGetSubscriberPreferencesResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        SubscribersControllerGetSubscriberPreferencesResponse res = sdk.subscribers().preferences().getPreferences()
                .subscriberId("<id>")
                .criticality(Criticality.NON_CRITICAL)
                .call();

        if (res.getSubscriberPreferencesDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                        | Type                                                             | Required                                                         | Description                                                      |
| ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| `subscriberId`                                                   | *String*                                                         | :heavy_check_mark:                                               | N/A                                                              |
| `criticality`                                                    | [Optional\<Criticality>](../../models/operations/Criticality.md) | :heavy_minus_sign:                                               | N/A                                                              |
| `idempotencyKey`                                                 | *Optional\<String>*                                              | :heavy_minus_sign:                                               | A header for idempotency purposes                                |

### Response

**[SubscribersControllerGetSubscriberPreferencesResponse](../../models/operations/SubscribersControllerGetSubscriberPreferencesResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |