# TranslationsMaster

## Overview

### Available Operations

* [retrieve](#retrieve) - Retrieve master translations JSON

## retrieve

Retrieve all translations for a locale in master JSON format organized by resourceId (workflowId)

### Example Usage

<!-- UsageSnippet language="java" operationID="TranslationController_getMasterJsonEndpoint" method="get" path="/v2/translations/master-json" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.operations.TranslationControllerGetMasterJsonEndpointResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        TranslationControllerGetMasterJsonEndpointResponse res = sdk.translationsMaster().retrieve()
                .locale("en_US")
                .call();

        if (res.getMasterJsonResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                              | Type                                                                   | Required                                                               | Description                                                            | Example                                                                |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `locale`                                                               | *Optional\<String>*                                                    | :heavy_minus_sign:                                                     | Locale to export. If not provided, exports organization default locale | en_US                                                                  |
| `idempotencyKey`                                                       | *Optional\<String>*                                                    | :heavy_minus_sign:                                                     | A header for idempotency purposes                                      |                                                                        |

### Response

**[TranslationControllerGetMasterJsonEndpointResponse](../../models/operations/TranslationControllerGetMasterJsonEndpointResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |