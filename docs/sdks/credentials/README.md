# Subscribers.Credentials

## Overview

### Available Operations

* [delete](#delete) - Delete provider credentials

## delete

Delete subscriber credentials for a provider such as **slack** and **FCM** by **providerId**. 
    This action is irreversible and will remove the credentials for the provider for particular **subscriberId**.

### Example Usage

<!-- UsageSnippet language="java" operationID="SubscribersV1Controller_deleteSubscriberCredentials" method="delete" path="/v1/subscribers/{subscriberId}/credentials/{providerId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.SubscribersV1ControllerDeleteSubscriberCredentialsResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        SubscribersV1ControllerDeleteSubscriberCredentialsResponse res = sdk.subscribers().credentials().delete()
                .subscriberId("<id>")
                .providerId("<id>")
                .call();

        // handle response
    }
}
```

### Parameters

| Parameter                         | Type                              | Required                          | Description                       |
| --------------------------------- | --------------------------------- | --------------------------------- | --------------------------------- |
| `subscriberId`                    | *String*                          | :heavy_check_mark:                | N/A                               |
| `providerId`                      | *String*                          | :heavy_check_mark:                | N/A                               |
| `idempotencyKey`                  | *Optional\<String>*               | :heavy_minus_sign:                | A header for idempotency purposes |

### Response

**[SubscribersV1ControllerDeleteSubscriberCredentialsResponse](../../models/operations/SubscribersV1ControllerDeleteSubscriberCredentialsResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |