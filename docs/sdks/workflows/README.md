# Workflows

## Overview

### Available Operations

* [create](#create) - Create a workflow
* [list](#list) - List all workflows
* [update](#update) - Update a workflow
* [get](#get) - Retrieve a workflow
* [delete](#delete) - Delete a workflow
* [modify](#modify) - Update a workflow
* [sync](#sync) - Sync a workflow
* [getStep](#getstep) - Retrieve workflow step

## create

Creates a new workflow in the Novu Cloud environment

### Example Usage

<!-- UsageSnippet language="java" operationID="WorkflowController_create" method="post" path="/v2/workflows" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import java.util.Map;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.WorkflowControllerCreateResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        WorkflowControllerCreateResponse res = sdk.workflows().create()
                .body(CreateWorkflowDto.builder()
                    .name("<value>")
                    .workflowId("<id>")
                    .steps(List.of())
                    .preferences(PreferencesRequestDto.builder()
                        .user(User.of(PreferencesRequestDtoWorkflowPreferencesDto.builder()
                            .all(PreferencesRequestDtoWorkflowPreferencesDtoAll.of(WorkflowPreferenceDto.builder()
                                .build()))
                            .channels(Map.ofEntries(
                                Map.entry("email", ChannelPreferenceDto.builder()
                                    .build()),
                                Map.entry("sms", ChannelPreferenceDto.builder()
                                    .enabled(false)
                                    .build())))
                            .build()))
                        .workflow(PreferencesRequestDtoWorkflow.builder()
                            .all(WorkflowAll.of(WorkflowPreferenceDto.builder()
                                .build()))
                            .channels(Map.ofEntries(
                                Map.entry("email", ChannelPreferenceDto.builder()
                                    .build()),
                                Map.entry("sms", ChannelPreferenceDto.builder()
                                    .enabled(false)
                                    .build())))
                            .build())
                        .build())
                    .build())
                .call();

        if (res.workflowResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                         | Type                                                              | Required                                                          | Description                                                       |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `idempotencyKey`                                                  | *Optional\<String>*                                               | :heavy_minus_sign:                                                | A header for idempotency purposes                                 |
| `body`                                                            | [CreateWorkflowDto](../../models/components/CreateWorkflowDto.md) | :heavy_check_mark:                                                | Workflow creation details                                         |

### Response

**[WorkflowControllerCreateResponse](../../models/operations/WorkflowControllerCreateResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## list

Retrieves a list of workflows with optional filtering and pagination

### Example Usage

<!-- UsageSnippet language="java" operationID="WorkflowController_searchWorkflows" method="get" path="/v2/workflows" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.WorkflowControllerSearchWorkflowsRequest;
import org.openapis.openapi.models.operations.WorkflowControllerSearchWorkflowsResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        WorkflowControllerSearchWorkflowsRequest req = WorkflowControllerSearchWorkflowsRequest.builder()
                .limit(10d)
                .offset(0d)
                .build();

        WorkflowControllerSearchWorkflowsResponse res = sdk.workflows().list()
                .request(req)
                .call();

        if (res.listWorkflowResponse().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                       | Type                                                                                                            | Required                                                                                                        | Description                                                                                                     |
| --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| `request`                                                                                                       | [WorkflowControllerSearchWorkflowsRequest](../../models/operations/WorkflowControllerSearchWorkflowsRequest.md) | :heavy_check_mark:                                                                                              | The request object to use for the request.                                                                      |

### Response

**[WorkflowControllerSearchWorkflowsResponse](../../models/operations/WorkflowControllerSearchWorkflowsResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## update

Updates the details of an existing workflow, here **workflowId** is the identifier of the workflow

### Example Usage

<!-- UsageSnippet language="java" operationID="WorkflowController_update" method="put" path="/v2/workflows/{workflowId}" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import java.util.Map;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.WorkflowControllerUpdateResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        WorkflowControllerUpdateResponse res = sdk.workflows().update()
                .workflowId("<id>")
                .body(UpdateWorkflowDto.builder()
                    .name("<value>")
                    .steps(List.of())
                    .preferences(PreferencesRequestDto.builder()
                        .user(User.of(PreferencesRequestDtoWorkflowPreferencesDto.builder()
                            .all(PreferencesRequestDtoWorkflowPreferencesDtoAll.of(WorkflowPreferenceDto.builder()
                                .build()))
                            .channels(Map.ofEntries(
                                Map.entry("email", ChannelPreferenceDto.builder()
                                    .build()),
                                Map.entry("sms", ChannelPreferenceDto.builder()
                                    .enabled(false)
                                    .build())))
                            .build()))
                        .workflow(PreferencesRequestDtoWorkflow.builder()
                            .all(WorkflowAll.of(WorkflowPreferenceDto.builder()
                                .build()))
                            .channels(Map.ofEntries(
                                Map.entry("email", ChannelPreferenceDto.builder()
                                    .build()),
                                Map.entry("sms", ChannelPreferenceDto.builder()
                                    .enabled(false)
                                    .build())))
                            .build())
                        .build())
                    .origin(ResourceOriginEnum.EXTERNAL)
                    .build())
                .call();

        if (res.workflowResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                         | Type                                                              | Required                                                          | Description                                                       |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `workflowId`                                                      | *String*                                                          | :heavy_check_mark:                                                | N/A                                                               |
| `idempotencyKey`                                                  | *Optional\<String>*                                               | :heavy_minus_sign:                                                | A header for idempotency purposes                                 |
| `body`                                                            | [UpdateWorkflowDto](../../models/components/UpdateWorkflowDto.md) | :heavy_check_mark:                                                | Workflow update details                                           |

### Response

**[WorkflowControllerUpdateResponse](../../models/operations/WorkflowControllerUpdateResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## get

Fetches details of a specific workflow by its unique identifier **workflowId**

### Example Usage

<!-- UsageSnippet language="java" operationID="WorkflowController_getWorkflow" method="get" path="/v2/workflows/{workflowId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.WorkflowControllerGetWorkflowResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        WorkflowControllerGetWorkflowResponse res = sdk.workflows().get()
                .workflowId("<id>")
                .call();

        if (res.workflowResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                         | Type                              | Required                          | Description                       |
| --------------------------------- | --------------------------------- | --------------------------------- | --------------------------------- |
| `workflowId`                      | *String*                          | :heavy_check_mark:                | N/A                               |
| `environmentId`                   | *Optional\<String>*               | :heavy_minus_sign:                | N/A                               |
| `idempotencyKey`                  | *Optional\<String>*               | :heavy_minus_sign:                | A header for idempotency purposes |

### Response

**[WorkflowControllerGetWorkflowResponse](../../models/operations/WorkflowControllerGetWorkflowResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## delete

Removes a specific workflow by its unique identifier **workflowId**

### Example Usage

<!-- UsageSnippet language="java" operationID="WorkflowController_removeWorkflow" method="delete" path="/v2/workflows/{workflowId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.WorkflowControllerRemoveWorkflowResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        WorkflowControllerRemoveWorkflowResponse res = sdk.workflows().delete()
                .workflowId("<id>")
                .call();

        // handle response
    }
}
```

### Parameters

| Parameter                         | Type                              | Required                          | Description                       |
| --------------------------------- | --------------------------------- | --------------------------------- | --------------------------------- |
| `workflowId`                      | *String*                          | :heavy_check_mark:                | N/A                               |
| `idempotencyKey`                  | *Optional\<String>*               | :heavy_minus_sign:                | A header for idempotency purposes |

### Response

**[WorkflowControllerRemoveWorkflowResponse](../../models/operations/WorkflowControllerRemoveWorkflowResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## modify

Partially updates a workflow by its unique identifier **workflowId**

### Example Usage

<!-- UsageSnippet language="java" operationID="WorkflowController_patchWorkflow" method="patch" path="/v2/workflows/{workflowId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.PatchWorkflowDto;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.WorkflowControllerPatchWorkflowResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        WorkflowControllerPatchWorkflowResponse res = sdk.workflows().modify()
                .workflowId("<id>")
                .body(PatchWorkflowDto.builder()
                    .build())
                .call();

        if (res.workflowResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                       | Type                                                            | Required                                                        | Description                                                     |
| --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- |
| `workflowId`                                                    | *String*                                                        | :heavy_check_mark:                                              | N/A                                                             |
| `idempotencyKey`                                                | *Optional\<String>*                                             | :heavy_minus_sign:                                              | A header for idempotency purposes                               |
| `body`                                                          | [PatchWorkflowDto](../../models/components/PatchWorkflowDto.md) | :heavy_check_mark:                                              | Workflow patch details                                          |

### Response

**[WorkflowControllerPatchWorkflowResponse](../../models/operations/WorkflowControllerPatchWorkflowResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## sync

Synchronizes a workflow to the target environment

### Example Usage

<!-- UsageSnippet language="java" operationID="WorkflowController_sync" method="put" path="/v2/workflows/{workflowId}/sync" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.SyncWorkflowDto;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.WorkflowControllerSyncResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        WorkflowControllerSyncResponse res = sdk.workflows().sync()
                .workflowId("<id>")
                .body(SyncWorkflowDto.builder()
                    .targetEnvironmentId("<id>")
                    .build())
                .call();

        if (res.workflowResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                     | Type                                                          | Required                                                      | Description                                                   |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| `workflowId`                                                  | *String*                                                      | :heavy_check_mark:                                            | N/A                                                           |
| `idempotencyKey`                                              | *Optional\<String>*                                           | :heavy_minus_sign:                                            | A header for idempotency purposes                             |
| `body`                                                        | [SyncWorkflowDto](../../models/components/SyncWorkflowDto.md) | :heavy_check_mark:                                            | Sync workflow details                                         |

### Response

**[WorkflowControllerSyncResponse](../../models/operations/WorkflowControllerSyncResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## getStep

Retrieves data for a specific step in a workflow

### Example Usage

<!-- UsageSnippet language="java" operationID="WorkflowController_getWorkflowStepData" method="get" path="/v2/workflows/{workflowId}/steps/{stepId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.WorkflowControllerGetWorkflowStepDataResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        WorkflowControllerGetWorkflowStepDataResponse res = sdk.workflows().getStep()
                .workflowId("<id>")
                .stepId("<id>")
                .call();

        if (res.stepResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                         | Type                              | Required                          | Description                       |
| --------------------------------- | --------------------------------- | --------------------------------- | --------------------------------- |
| `workflowId`                      | *String*                          | :heavy_check_mark:                | N/A                               |
| `stepId`                          | *String*                          | :heavy_check_mark:                | N/A                               |
| `idempotencyKey`                  | *Optional\<String>*               | :heavy_minus_sign:                | A header for idempotency purposes |

### Response

**[WorkflowControllerGetWorkflowStepDataResponse](../../models/operations/WorkflowControllerGetWorkflowStepDataResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |