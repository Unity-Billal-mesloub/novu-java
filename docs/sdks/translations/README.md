# Translations

## Overview

### Available Operations

* [create](#create) - Create a translation
* [get](#get) - Retrieve a translation
* [delete](#delete) - Delete a translation
* [upload](#upload) - Upload translation files
* [importMasterJson](#importmasterjson) - Import master translations JSON
* [uploadMasterJson](#uploadmasterjson) - Upload master translations JSON file

## create

Create a translation for a specific workflow and locale, if the translation already exists, it will be updated

### Example Usage

<!-- UsageSnippet language="java" operationID="TranslationController_createTranslationEndpoint" method="post" path="/v2/translations" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.Map;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.CreateTranslationRequestDto;
import org.openapis.openapi.models.components.CreateTranslationRequestDtoResourceType;
import org.openapis.openapi.models.operations.TranslationControllerCreateTranslationEndpointResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        TranslationControllerCreateTranslationEndpointResponse res = sdk.translations().create()
                .body(CreateTranslationRequestDto.builder()
                    .resourceId("welcome-email")
                    .resourceType(CreateTranslationRequestDtoResourceType.LAYOUT)
                    .locale("en_US")
                    .content(Map.ofEntries(
                        Map.entry("welcome.title", "Welcome"),
                        Map.entry("welcome.message", "Hello there!")))
                    .build())
                .call();

        if (res.translationResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                             | Type                                                                                  | Required                                                                              | Description                                                                           |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `idempotencyKey`                                                                      | *Optional\<String>*                                                                   | :heavy_minus_sign:                                                                    | A header for idempotency purposes                                                     |
| `body`                                                                                | [CreateTranslationRequestDto](../../models/components/CreateTranslationRequestDto.md) | :heavy_check_mark:                                                                    | N/A                                                                                   |

### Response

**[TranslationControllerCreateTranslationEndpointResponse](../../models/operations/TranslationControllerCreateTranslationEndpointResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## get

Retrieve a specific translation by resource type, resource ID and locale

### Example Usage

<!-- UsageSnippet language="java" operationID="TranslationController_getSingleTranslation" method="get" path="/v2/translations/{resourceType}/{resourceId}/{locale}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.operations.TranslationControllerGetSingleTranslationResourceType;
import org.openapis.openapi.models.operations.TranslationControllerGetSingleTranslationResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        TranslationControllerGetSingleTranslationResponse res = sdk.translations().get()
                .resourceType(TranslationControllerGetSingleTranslationResourceType.LAYOUT)
                .resourceId("welcome-email")
                .locale("en_US")
                .call();

        if (res.translationResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                                 | Type                                                                                                                                      | Required                                                                                                                                  | Description                                                                                                                               | Example                                                                                                                                   |
| ----------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| `resourceType`                                                                                                                            | [TranslationControllerGetSingleTranslationResourceType](../../models/operations/TranslationControllerGetSingleTranslationResourceType.md) | :heavy_check_mark:                                                                                                                        | Resource type                                                                                                                             |                                                                                                                                           |
| `resourceId`                                                                                                                              | *String*                                                                                                                                  | :heavy_check_mark:                                                                                                                        | Resource ID                                                                                                                               | welcome-email                                                                                                                             |
| `locale`                                                                                                                                  | *String*                                                                                                                                  | :heavy_check_mark:                                                                                                                        | Locale code                                                                                                                               | en_US                                                                                                                                     |
| `idempotencyKey`                                                                                                                          | *Optional\<String>*                                                                                                                       | :heavy_minus_sign:                                                                                                                        | A header for idempotency purposes                                                                                                         |                                                                                                                                           |

### Response

**[TranslationControllerGetSingleTranslationResponse](../../models/operations/TranslationControllerGetSingleTranslationResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## delete

Delete a specific translation by resource type, resource ID and locale

### Example Usage

<!-- UsageSnippet language="java" operationID="TranslationController_deleteTranslationEndpoint" method="delete" path="/v2/translations/{resourceType}/{resourceId}/{locale}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.operations.TranslationControllerDeleteTranslationEndpointResourceType;
import org.openapis.openapi.models.operations.TranslationControllerDeleteTranslationEndpointResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        TranslationControllerDeleteTranslationEndpointResponse res = sdk.translations().delete()
                .resourceType(TranslationControllerDeleteTranslationEndpointResourceType.LAYOUT)
                .resourceId("<id>")
                .locale("pl")
                .call();

        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                                           | Type                                                                                                                                                | Required                                                                                                                                            | Description                                                                                                                                         |
| --------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| `resourceType`                                                                                                                                      | [TranslationControllerDeleteTranslationEndpointResourceType](../../models/operations/TranslationControllerDeleteTranslationEndpointResourceType.md) | :heavy_check_mark:                                                                                                                                  | Resource type                                                                                                                                       |
| `resourceId`                                                                                                                                        | *String*                                                                                                                                            | :heavy_check_mark:                                                                                                                                  | Resource ID                                                                                                                                         |
| `locale`                                                                                                                                            | *String*                                                                                                                                            | :heavy_check_mark:                                                                                                                                  | Locale code                                                                                                                                         |
| `idempotencyKey`                                                                                                                                    | *Optional\<String>*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                  | A header for idempotency purposes                                                                                                                   |

### Response

**[TranslationControllerDeleteTranslationEndpointResponse](../../models/operations/TranslationControllerDeleteTranslationEndpointResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## upload

Upload one or more JSON translation files for a specific workflow. Files name must match the locale, e.g. en_US.json. Supports both "files" and "files[]" field names for backwards compatibility.

### Example Usage

<!-- UsageSnippet language="java" operationID="TranslationController_uploadTranslationFiles" method="post" path="/v2/translations/upload" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.operations.*;

public class Application {

    public static void main(String[] args) throws Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        TranslationControllerUploadTranslationFilesResponse res = sdk.translations().upload()
                .body(TranslationControllerUploadTranslationFilesRequestBody.builder()
                    .resourceId("welcome-email")
                    .resourceType(TranslationControllerUploadTranslationFilesResourceType.WORKFLOW)
                    .files(List.of())
                    .build())
                .call();

    }
}
```

### Parameters

| Parameter                                                                                                                                   | Type                                                                                                                                        | Required                                                                                                                                    | Description                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| `idempotencyKey`                                                                                                                            | *Optional\<String>*                                                                                                                         | :heavy_minus_sign:                                                                                                                          | A header for idempotency purposes                                                                                                           |
| `body`                                                                                                                                      | [TranslationControllerUploadTranslationFilesRequestBody](../../models/operations/TranslationControllerUploadTranslationFilesRequestBody.md) | :heavy_check_mark:                                                                                                                          | N/A                                                                                                                                         |

### Response

**[TranslationControllerUploadTranslationFilesResponse](../../models/operations/TranslationControllerUploadTranslationFilesResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## importMasterJson

Import translations for multiple workflows from master JSON format for a specific locale

### Example Usage

<!-- UsageSnippet language="java" operationID="TranslationController_importMasterJsonEndpoint" method="post" path="/v2/translations/master-json" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.Map;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.ImportMasterJsonRequestDto;
import org.openapis.openapi.models.operations.TranslationControllerImportMasterJsonEndpointResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        TranslationControllerImportMasterJsonEndpointResponse res = sdk.translations().importMasterJson()
                .body(ImportMasterJsonRequestDto.builder()
                    .locale("en_US")
                    .masterJson(Map.ofEntries(
                        Map.entry("workflows", Map.ofEntries(
                            Map.entry("welcome-email", Map.ofEntries(
                                Map.entry("welcome.title", "Welcome to our platform"),
                                Map.entry("welcome.message", "Hello there!"))),
                            Map.entry("password-reset", Map.ofEntries(
                                Map.entry("reset.title", "Reset your password"),
                                Map.entry("reset.message", "Click the link to reset")))))))
                    .build())
                .call();

        if (res.importMasterJsonResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                           | Type                                                                                | Required                                                                            | Description                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `idempotencyKey`                                                                    | *Optional\<String>*                                                                 | :heavy_minus_sign:                                                                  | A header for idempotency purposes                                                   |
| `body`                                                                              | [ImportMasterJsonRequestDto](../../models/components/ImportMasterJsonRequestDto.md) | :heavy_check_mark:                                                                  | N/A                                                                                 |

### Response

**[TranslationControllerImportMasterJsonEndpointResponse](../../models/operations/TranslationControllerImportMasterJsonEndpointResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## uploadMasterJson

Upload a master JSON file containing translations for multiple workflows. Locale is automatically detected from filename (e.g., en_US.json)

### Example Usage

<!-- UsageSnippet language="java" operationID="TranslationController_uploadMasterJsonEndpoint" method="post" path="/v2/translations/master-json/upload" -->
```java
package hello.world;

import java.lang.Exception;
import java.nio.file.Paths;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.operations.*;
import org.openapis.openapi.utils.Blob;

public class Application {

    public static void main(String[] args) throws Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        TranslationControllerUploadMasterJsonEndpointResponse res = sdk.translations().uploadMasterJson()
                .body(TranslationControllerUploadMasterJsonEndpointRequestBody.builder()
                    .file(TranslationControllerUploadMasterJsonEndpointFile.builder()
                        .fileName("example.file")
                        .content(Blob.from(Paths.get("example.file")))
                        .build())
                    .build())
                .call();

    }
}
```

### Parameters

| Parameter                                                                                                                                       | Type                                                                                                                                            | Required                                                                                                                                        | Description                                                                                                                                     |
| ----------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| `idempotencyKey`                                                                                                                                | *Optional\<String>*                                                                                                                             | :heavy_minus_sign:                                                                                                                              | A header for idempotency purposes                                                                                                               |
| `body`                                                                                                                                          | [TranslationControllerUploadMasterJsonEndpointRequestBody](../../models/operations/TranslationControllerUploadMasterJsonEndpointRequestBody.md) | :heavy_check_mark:                                                                                                                              | N/A                                                                                                                                             |

### Response

**[TranslationControllerUploadMasterJsonEndpointResponse](../../models/operations/TranslationControllerUploadMasterJsonEndpointResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |