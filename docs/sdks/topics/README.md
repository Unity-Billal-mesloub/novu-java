# Topics

## Overview

### Available Operations

* [getAll](#getall) - List all topics
* [create](#create) - Create a topic
* [getTopic](#gettopic) - Retrieve a topic
* [patch](#patch) - Update a topic
* [remove](#remove) - Delete a topic
* [createSubscription](#createsubscription) - Create topic subscriptions

## getAll

This api returns a paginated list of topics.
    Topics can be filtered by **key**, **name**, or **includeCursor** to paginate through the list. 
    Checkout all available filters in the query section.

### Example Usage

<!-- UsageSnippet language="java" operationID="TopicsController_listTopics" method="get" path="/v2/topics" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.TopicsControllerListTopicsRequest;
import org.openapis.openapi.models.operations.TopicsControllerListTopicsResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        TopicsControllerListTopicsRequest req = TopicsControllerListTopicsRequest.builder()
                .limit(10d)
                .build();

        TopicsControllerListTopicsResponse res = sdk.topics().getAll()
                .request(req)
                .call();

        if (res.listTopicsResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                         | Type                                                                                              | Required                                                                                          | Description                                                                                       |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| `request`                                                                                         | [TopicsControllerListTopicsRequest](../../models/operations/TopicsControllerListTopicsRequest.md) | :heavy_check_mark:                                                                                | The request object to use for the request.                                                        |

### Response

**[TopicsControllerListTopicsResponse](../../models/operations/TopicsControllerListTopicsResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## create

Creates a new topic if it does not exist, or updates an existing topic if it already exists. Use ?failIfExists=true to prevent updates.

### Example Usage

<!-- UsageSnippet language="java" operationID="TopicsController_upsertTopic" method="post" path="/v2/topics" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.CreateUpdateTopicRequestDto;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.TopicsControllerUpsertTopicResponse;

public class Application {

    public static void main(String[] args) throws TopicResponseDtoException, ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        TopicsControllerUpsertTopicResponse res = sdk.topics().create()
                .body(CreateUpdateTopicRequestDto.builder()
                    .key("task:12345")
                    .name("Task Title")
                    .build())
                .call();

        if (res.topicResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                             | Type                                                                                  | Required                                                                              | Description                                                                           |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `failIfExists`                                                                        | *Optional\<Boolean>*                                                                  | :heavy_minus_sign:                                                                    | If true, the request will fail if a topic with the same key already exists            |
| `idempotencyKey`                                                                      | *Optional\<String>*                                                                   | :heavy_minus_sign:                                                                    | A header for idempotency purposes                                                     |
| `body`                                                                                | [CreateUpdateTopicRequestDto](../../models/components/CreateUpdateTopicRequestDto.md) | :heavy_check_mark:                                                                    | N/A                                                                                   |

### Response

**[TopicsControllerUpsertTopicResponse](../../models/operations/TopicsControllerUpsertTopicResponse.md)**

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| models/errors/TopicResponseDtoException | 409                                     | application/json                        |
| models/errors/ErrorDto                  | 414                                     | application/json                        |
| models/errors/ErrorDto                  | 400, 401, 403, 404, 405, 413, 415       | application/json                        |
| models/errors/ValidationErrorDto        | 422                                     | application/json                        |
| models/errors/ErrorDto                  | 500                                     | application/json                        |
| models/errors/APIException              | 4XX, 5XX                                | \*/\*                                   |

## getTopic

Retrieve a topic by its unique key identifier **topicKey**

### Example Usage

<!-- UsageSnippet language="java" operationID="TopicsController_getTopic" method="get" path="/v2/topics/{topicKey}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.TopicsControllerGetTopicResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        TopicsControllerGetTopicResponse res = sdk.topics().getTopic()
                .topicKey("<value>")
                .call();

        if (res.topicResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                         | Type                              | Required                          | Description                       |
| --------------------------------- | --------------------------------- | --------------------------------- | --------------------------------- |
| `topicKey`                        | *String*                          | :heavy_check_mark:                | The key identifier of the topic   |
| `idempotencyKey`                  | *Optional\<String>*               | :heavy_minus_sign:                | A header for idempotency purposes |

### Response

**[TopicsControllerGetTopicResponse](../../models/operations/TopicsControllerGetTopicResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## patch

Update a topic name by its unique key identifier **topicKey**

### Example Usage

<!-- UsageSnippet language="java" operationID="TopicsController_updateTopic" method="patch" path="/v2/topics/{topicKey}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.UpdateTopicRequestDto;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.TopicsControllerUpdateTopicResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        TopicsControllerUpdateTopicResponse res = sdk.topics().patch()
                .topicKey("<value>")
                .body(UpdateTopicRequestDto.builder()
                    .name("Updated Topic Name")
                    .build())
                .call();

        if (res.topicResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `topicKey`                                                                | *String*                                                                  | :heavy_check_mark:                                                        | The key identifier of the topic                                           |
| `idempotencyKey`                                                          | *Optional\<String>*                                                       | :heavy_minus_sign:                                                        | A header for idempotency purposes                                         |
| `body`                                                                    | [UpdateTopicRequestDto](../../models/components/UpdateTopicRequestDto.md) | :heavy_check_mark:                                                        | N/A                                                                       |

### Response

**[TopicsControllerUpdateTopicResponse](../../models/operations/TopicsControllerUpdateTopicResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## remove

Delete a topic by its unique key identifier **topicKey**. 
    This action is irreversible and will remove all subscriptions to the topic.

### Example Usage

<!-- UsageSnippet language="java" operationID="TopicsController_deleteTopic" method="delete" path="/v2/topics/{topicKey}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.TopicsControllerDeleteTopicResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        TopicsControllerDeleteTopicResponse res = sdk.topics().remove()
                .topicKey("<value>")
                .call();

        if (res.deleteTopicResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                         | Type                              | Required                          | Description                       |
| --------------------------------- | --------------------------------- | --------------------------------- | --------------------------------- |
| `topicKey`                        | *String*                          | :heavy_check_mark:                | The key identifier of the topic   |
| `idempotencyKey`                  | *Optional\<String>*               | :heavy_minus_sign:                | A header for idempotency purposes |

### Response

**[TopicsControllerDeleteTopicResponse](../../models/operations/TopicsControllerDeleteTopicResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## createSubscription

This api will create subscription for subscriberIds for a topic. 
      Its like subscribing to a common interest group. if topic does not exist, it will be created.

### Example Usage

<!-- UsageSnippet language="java" operationID="TopicsController_createTopicSubscriptions" method="post" path="/v2/topics/{topicKey}/subscriptions" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import java.util.Map;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.TopicsControllerCreateTopicSubscriptionsResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        TopicsControllerCreateTopicSubscriptionsResponse res = sdk.topics().createSubscription()
                .topicKey("<value>")
                .body(CreateTopicSubscriptionsRequestDto.builder()
                    .subscriptions(List.of(
                        CreateTopicSubscriptionsRequestDtoSubscription.of(TopicSubscriberIdentifierDto.builder()
                            .identifier("subscriber-123-subscription-a")
                            .subscriberId("subscriber-123")
                            .build()),
                        CreateTopicSubscriptionsRequestDtoSubscription.of(TopicSubscriberIdentifierDto.builder()
                            .identifier("subscriber-456-subscription-b")
                            .subscriberId("subscriber-456")
                            .build())))
                    .name("My Topic")
                    .preferences(List.of(
                        CreateTopicSubscriptionsRequestDtoPreference.of(WorkflowPreferenceRequestDto.builder()
                            .workflowId("workflow-123")
                            .condition(Map.ofEntries(
                                Map.entry("===", List.of(
                                    Map.ofEntries(
                                        Map.entry("var", "tier")),
                                    "premium"))))
                            .build())))
                    .build())
                .call();

        if (res.createSubscriptionsResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                           | Type                                                                                                | Required                                                                                            | Description                                                                                         |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `topicKey`                                                                                          | *String*                                                                                            | :heavy_check_mark:                                                                                  | The key identifier of the topic                                                                     |
| `idempotencyKey`                                                                                    | *Optional\<String>*                                                                                 | :heavy_minus_sign:                                                                                  | A header for idempotency purposes                                                                   |
| `body`                                                                                              | [CreateTopicSubscriptionsRequestDto](../../models/components/CreateTopicSubscriptionsRequestDto.md) | :heavy_check_mark:                                                                                  | N/A                                                                                                 |

### Response

**[TopicsControllerCreateTopicSubscriptionsResponse](../../models/operations/TopicsControllerCreateTopicSubscriptionsResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |