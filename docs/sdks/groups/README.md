# Translations.Groups

## Overview

### Available Operations

* [removeGroup](#removegroup) - Delete a translation group
* [fetchGroup](#fetchgroup) - Retrieve a translation group

## removeGroup

Delete an entire translation group and all its translations

### Example Usage

<!-- UsageSnippet language="java" operationID="TranslationController_deleteTranslationGroupEndpoint" method="delete" path="/v2/translations/{resourceType}/{resourceId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.operations.TranslationControllerDeleteTranslationGroupEndpointResourceType;
import org.openapis.openapi.models.operations.TranslationControllerDeleteTranslationGroupEndpointResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        TranslationControllerDeleteTranslationGroupEndpointResponse res = sdk.translations().groups().removeGroup()
                .resourceType(TranslationControllerDeleteTranslationGroupEndpointResourceType.WORKFLOW)
                .resourceId("welcome-email")
                .call();

        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                                                     | Type                                                                                                                                                          | Required                                                                                                                                                      | Description                                                                                                                                                   | Example                                                                                                                                                       |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `resourceType`                                                                                                                                                | [TranslationControllerDeleteTranslationGroupEndpointResourceType](../../models/operations/TranslationControllerDeleteTranslationGroupEndpointResourceType.md) | :heavy_check_mark:                                                                                                                                            | Resource type                                                                                                                                                 | workflow                                                                                                                                                      |
| `resourceId`                                                                                                                                                  | *String*                                                                                                                                                      | :heavy_check_mark:                                                                                                                                            | Resource ID                                                                                                                                                   | welcome-email                                                                                                                                                 |
| `idempotencyKey`                                                                                                                                              | *Optional\<String>*                                                                                                                                           | :heavy_minus_sign:                                                                                                                                            | A header for idempotency purposes                                                                                                                             |                                                                                                                                                               |

### Response

**[TranslationControllerDeleteTranslationGroupEndpointResponse](../../models/operations/TranslationControllerDeleteTranslationGroupEndpointResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## fetchGroup

Retrieves a single translation group by resource type (workflow, layout) and resource ID (workflowId, layoutId)

### Example Usage

<!-- UsageSnippet language="java" operationID="TranslationController_getTranslationGroupEndpoint" method="get" path="/v2/translations/group/{resourceType}/{resourceId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.operations.TranslationControllerGetTranslationGroupEndpointResourceType;
import org.openapis.openapi.models.operations.TranslationControllerGetTranslationGroupEndpointResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        TranslationControllerGetTranslationGroupEndpointResponse res = sdk.translations().groups().fetchGroup()
                .resourceType(TranslationControllerGetTranslationGroupEndpointResourceType.WORKFLOW)
                .resourceId("welcome-email")
                .call();

        if (res.translationGroupDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                                               | Type                                                                                                                                                    | Required                                                                                                                                                | Description                                                                                                                                             | Example                                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `resourceType`                                                                                                                                          | [TranslationControllerGetTranslationGroupEndpointResourceType](../../models/operations/TranslationControllerGetTranslationGroupEndpointResourceType.md) | :heavy_check_mark:                                                                                                                                      | Resource type                                                                                                                                           | workflow                                                                                                                                                |
| `resourceId`                                                                                                                                            | *String*                                                                                                                                                | :heavy_check_mark:                                                                                                                                      | Resource ID                                                                                                                                             | welcome-email                                                                                                                                           |
| `idempotencyKey`                                                                                                                                        | *Optional\<String>*                                                                                                                                     | :heavy_minus_sign:                                                                                                                                      | A header for idempotency purposes                                                                                                                       |                                                                                                                                                         |

### Response

**[TranslationControllerGetTranslationGroupEndpointResponse](../../models/operations/TranslationControllerGetTranslationGroupEndpointResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |