# Subscribers

## Overview

### Available Operations

* [search](#search) - Search subscribers
* [create](#create) - Create a subscriber
* [get](#get) - Retrieve a subscriber
* [update](#update) - Update a subscriber
* [removeSubscriber](#removesubscriber) - Delete a subscriber
* [createBulk](#createbulk) - Bulk create subscribers
* [updatePreferences](#updatepreferences) - Update subscriber preferences
* [updateCredentials](#updatecredentials) - Update provider credentials
* [appendCredentials](#appendcredentials) - Upsert provider credentials
* [markAllMessagesAs](#markallmessagesas) - Update notifications state
* [getUnseenCount](#getunseencount) - Retrieve unseen notifications count
* [updateOnlineStatus](#updateonlinestatus) - Update subscriber online status

## search

Search subscribers by their **email**, **phone**, **subscriberId** and **name**. 
    The search is case sensitive and supports pagination.Checkout all available filters in the query section.

### Example Usage

<!-- UsageSnippet language="java" operationID="SubscribersController_searchSubscribers" method="get" path="/v2/subscribers" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.SubscribersControllerSearchSubscribersRequest;
import org.openapis.openapi.models.operations.SubscribersControllerSearchSubscribersResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        SubscribersControllerSearchSubscribersRequest req = SubscribersControllerSearchSubscribersRequest.builder()
                .limit(10d)
                .build();

        SubscribersControllerSearchSubscribersResponse res = sdk.subscribers().search()
                .request(req)
                .call();

        if (res.listSubscribersResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                 | Type                                                                                                                      | Required                                                                                                                  | Description                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `request`                                                                                                                 | [SubscribersControllerSearchSubscribersRequest](../../models/operations/SubscribersControllerSearchSubscribersRequest.md) | :heavy_check_mark:                                                                                                        | The request object to use for the request.                                                                                |

### Response

**[SubscribersControllerSearchSubscribersResponse](../../models/operations/SubscribersControllerSearchSubscribersResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## create

Create a subscriber with the subscriber attributes. 
      **subscriberId** is a required field, rest other fields are optional, if the subscriber already exists, it will be updated

### Example Usage

<!-- UsageSnippet language="java" operationID="SubscribersController_createSubscriber" method="post" path="/v2/subscribers" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.CreateSubscriberRequestDto;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.SubscribersControllerCreateSubscriberResponse;

public class Application {

    public static void main(String[] args) throws SubscriberResponseDtoException, ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        SubscribersControllerCreateSubscriberResponse res = sdk.subscribers().create()
                .body(CreateSubscriberRequestDto.builder()
                    .subscriberId("<id>")
                    .firstName("John")
                    .lastName("Doe")
                    .email("john.doe@example.com")
                    .phone("+1234567890")
                    .avatar("https://example.com/avatar.jpg")
                    .locale("en-US")
                    .timezone("America/New_York")
                    .build())
                .call();

        if (res.subscriberResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                | Type                                                                                     | Required                                                                                 | Description                                                                              |
| ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| `failIfExists`                                                                           | *Optional\<Boolean>*                                                                     | :heavy_minus_sign:                                                                       | If true, the request will fail if a subscriber with the same subscriberId already exists |
| `idempotencyKey`                                                                         | *Optional\<String>*                                                                      | :heavy_minus_sign:                                                                       | A header for idempotency purposes                                                        |
| `body`                                                                                   | [CreateSubscriberRequestDto](../../models/components/CreateSubscriberRequestDto.md)      | :heavy_check_mark:                                                                       | N/A                                                                                      |

### Response

**[SubscribersControllerCreateSubscriberResponse](../../models/operations/SubscribersControllerCreateSubscriberResponse.md)**

### Errors

| Error Type                                   | Status Code                                  | Content Type                                 |
| -------------------------------------------- | -------------------------------------------- | -------------------------------------------- |
| models/errors/SubscriberResponseDtoException | 409                                          | application/json                             |
| models/errors/ErrorDto                       | 414                                          | application/json                             |
| models/errors/ErrorDto                       | 400, 401, 403, 404, 405, 413, 415            | application/json                             |
| models/errors/ValidationErrorDto             | 422                                          | application/json                             |
| models/errors/ErrorDto                       | 500                                          | application/json                             |
| models/errors/APIException                   | 4XX, 5XX                                     | \*/\*                                        |

## get

Retrieve a subscriber by its unique key identifier **subscriberId**. 
    **subscriberId** field is required.

### Example Usage

<!-- UsageSnippet language="java" operationID="SubscribersController_getSubscriber" method="get" path="/v2/subscribers/{subscriberId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.SubscribersControllerGetSubscriberResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        SubscribersControllerGetSubscriberResponse res = sdk.subscribers().get()
                .subscriberId("<id>")
                .call();

        if (res.subscriberResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                         | Type                              | Required                          | Description                       |
| --------------------------------- | --------------------------------- | --------------------------------- | --------------------------------- |
| `subscriberId`                    | *String*                          | :heavy_check_mark:                | N/A                               |
| `idempotencyKey`                  | *Optional\<String>*               | :heavy_minus_sign:                | A header for idempotency purposes |

### Response

**[SubscribersControllerGetSubscriberResponse](../../models/operations/SubscribersControllerGetSubscriberResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## update

Update a subscriber by its unique key identifier **subscriberId**. 
    **subscriberId** is a required field, rest other fields are optional

### Example Usage

<!-- UsageSnippet language="java" operationID="SubscribersController_patchSubscriber" method="patch" path="/v2/subscribers/{subscriberId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.PatchSubscriberRequestDto;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.SubscribersControllerPatchSubscriberResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        SubscribersControllerPatchSubscriberResponse res = sdk.subscribers().update()
                .subscriberId("<id>")
                .body(PatchSubscriberRequestDto.builder()
                    .firstName("John")
                    .lastName("Doe")
                    .email("john.doe@example.com")
                    .phone("+1234567890")
                    .avatar("https://example.com/avatar.jpg")
                    .locale("en-US")
                    .timezone("America/New_York")
                    .build())
                .call();

        if (res.subscriberResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                         | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `subscriberId`                                                                    | *String*                                                                          | :heavy_check_mark:                                                                | N/A                                                                               |
| `idempotencyKey`                                                                  | *Optional\<String>*                                                               | :heavy_minus_sign:                                                                | A header for idempotency purposes                                                 |
| `body`                                                                            | [PatchSubscriberRequestDto](../../models/components/PatchSubscriberRequestDto.md) | :heavy_check_mark:                                                                | N/A                                                                               |

### Response

**[SubscribersControllerPatchSubscriberResponse](../../models/operations/SubscribersControllerPatchSubscriberResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## removeSubscriber

Deletes a subscriber entity from the Novu platform along with associated messages, preferences, and topic subscriptions. 
      **subscriberId** is a required field.

### Example Usage

<!-- UsageSnippet language="java" operationID="SubscribersController_removeSubscriber" method="delete" path="/v2/subscribers/{subscriberId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.SubscribersControllerRemoveSubscriberResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        SubscribersControllerRemoveSubscriberResponse res = sdk.subscribers().removeSubscriber()
                .subscriberId("<id>")
                .call();

        if (res.removeSubscriberResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                         | Type                              | Required                          | Description                       |
| --------------------------------- | --------------------------------- | --------------------------------- | --------------------------------- |
| `subscriberId`                    | *String*                          | :heavy_check_mark:                | N/A                               |
| `idempotencyKey`                  | *Optional\<String>*               | :heavy_minus_sign:                | A header for idempotency purposes |

### Response

**[SubscribersControllerRemoveSubscriberResponse](../../models/operations/SubscribersControllerRemoveSubscriberResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## createBulk


      Using this endpoint multiple subscribers can be created at once. The bulk API is limited to 500 subscribers per request.
    

### Example Usage

<!-- UsageSnippet language="java" operationID="SubscribersV1Controller_bulkCreateSubscribers" method="post" path="/v1/subscribers/bulk" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.BulkSubscriberCreateDto;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.SubscribersV1ControllerBulkCreateSubscribersResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        SubscribersV1ControllerBulkCreateSubscribersResponse res = sdk.subscribers().createBulk()
                .body(BulkSubscriberCreateDto.builder()
                    .subscribers(List.of())
                    .build())
                .call();

        if (res.bulkCreateSubscriberResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `idempotencyKey`                                                              | *Optional\<String>*                                                           | :heavy_minus_sign:                                                            | A header for idempotency purposes                                             |
| `body`                                                                        | [BulkSubscriberCreateDto](../../models/components/BulkSubscriberCreateDto.md) | :heavy_check_mark:                                                            | N/A                                                                           |

### Response

**[SubscribersV1ControllerBulkCreateSubscribersResponse](../../models/operations/SubscribersV1ControllerBulkCreateSubscribersResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## updatePreferences

Update subscriber preferences by its unique key identifier **subscriberId**. 
    **workflowId** is optional field, if provided, this API will update that workflow preference, 
    otherwise it will update global preferences

### Example Usage

<!-- UsageSnippet language="java" operationID="SubscribersController_updateSubscriberPreferences" method="patch" path="/v2/subscribers/{subscriberId}/preferences" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.SubscribersControllerUpdateSubscriberPreferencesResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        SubscribersControllerUpdateSubscriberPreferencesResponse res = sdk.subscribers().updatePreferences()
                .subscriberId("<id>")
                .body(PatchSubscriberPreferencesDto.builder()
                    .schedule(ScheduleDto.builder()
                        .isEnabled(true)
                        .weeklySchedule(WeeklySchedule.builder()
                            .monday(Monday.builder()
                                .isEnabled(true)
                                .hours(List.of(
                                    TimeRangeDto.builder()
                                        .start("09:00 AM")
                                        .end("05:00 PM")
                                        .build()))
                                .build())
                            .tuesday(Tuesday.builder()
                                .isEnabled(true)
                                .hours(List.of(
                                    TimeRangeDto.builder()
                                        .start("09:00 AM")
                                        .end("05:00 PM")
                                        .build()))
                                .build())
                            .wednesday(Wednesday.builder()
                                .isEnabled(true)
                                .hours(List.of(
                                    TimeRangeDto.builder()
                                        .start("09:00 AM")
                                        .end("05:00 PM")
                                        .build()))
                                .build())
                            .thursday(Thursday.builder()
                                .isEnabled(true)
                                .hours(List.of(
                                    TimeRangeDto.builder()
                                        .start("09:00 AM")
                                        .end("05:00 PM")
                                        .build()))
                                .build())
                            .friday(Friday.builder()
                                .isEnabled(true)
                                .hours(List.of(
                                    TimeRangeDto.builder()
                                        .start("09:00 AM")
                                        .end("05:00 PM")
                                        .build()))
                                .build())
                            .saturday(Saturday.builder()
                                .isEnabled(true)
                                .hours(List.of(
                                    TimeRangeDto.builder()
                                        .start("09:00 AM")
                                        .end("05:00 PM")
                                        .build()))
                                .build())
                            .sunday(Sunday.builder()
                                .isEnabled(true)
                                .hours(List.of(
                                    TimeRangeDto.builder()
                                        .start("09:00 AM")
                                        .end("05:00 PM")
                                        .build()))
                                .build())
                            .build())
                        .build())
                    .build())
                .call();

        if (res.getSubscriberPreferencesDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                 | Type                                                                                      | Required                                                                                  | Description                                                                               |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `subscriberId`                                                                            | *String*                                                                                  | :heavy_check_mark:                                                                        | N/A                                                                                       |
| `idempotencyKey`                                                                          | *Optional\<String>*                                                                       | :heavy_minus_sign:                                                                        | A header for idempotency purposes                                                         |
| `body`                                                                                    | [PatchSubscriberPreferencesDto](../../models/components/PatchSubscriberPreferencesDto.md) | :heavy_check_mark:                                                                        | N/A                                                                                       |

### Response

**[SubscribersControllerUpdateSubscriberPreferencesResponse](../../models/operations/SubscribersControllerUpdateSubscriberPreferencesResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## updateCredentials

Update credentials for a provider such as **slack** and **FCM**. 
      **providerId** is required field. This API creates the **deviceTokens** or replaces the existing ones.

### Example Usage

<!-- UsageSnippet language="java" operationID="SubscribersV1Controller_updateSubscriberChannel" method="put" path="/v1/subscribers/{subscriberId}/credentials" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.SubscribersV1ControllerUpdateSubscriberChannelResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        SubscribersV1ControllerUpdateSubscriberChannelResponse res = sdk.subscribers().updateCredentials()
                .subscriberId("<id>")
                .body(UpdateSubscriberChannelRequestDto.builder()
                    .providerId(ChatOrPushProviderEnum.SLACK)
                    .credentials(ChannelCredentials.builder()
                        .webhookUrl("https://example.com/webhook")
                        .channel("general")
                        .deviceTokens(List.of(
                            "token1",
                            "token2",
                            "token3"))
                        .alertUid("12345-abcde")
                        .title("Critical Alert")
                        .imageUrl("https://example.com/image.png")
                        .state("resolved")
                        .externalUrl("https://example.com/details")
                        .build())
                    .build())
                .call();

        if (res.subscriberResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                         | Type                                                                                              | Required                                                                                          | Description                                                                                       |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| `subscriberId`                                                                                    | *String*                                                                                          | :heavy_check_mark:                                                                                | N/A                                                                                               |
| `idempotencyKey`                                                                                  | *Optional\<String>*                                                                               | :heavy_minus_sign:                                                                                | A header for idempotency purposes                                                                 |
| `body`                                                                                            | [UpdateSubscriberChannelRequestDto](../../models/components/UpdateSubscriberChannelRequestDto.md) | :heavy_check_mark:                                                                                | N/A                                                                                               |

### Response

**[SubscribersV1ControllerUpdateSubscriberChannelResponse](../../models/operations/SubscribersV1ControllerUpdateSubscriberChannelResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## appendCredentials

Upsert credentials for a provider such as **slack** and **FCM**. 
      **providerId** is required field. This API creates **deviceTokens** or appends to the existing ones.

### Example Usage

<!-- UsageSnippet language="java" operationID="SubscribersV1Controller_modifySubscriberChannel" method="patch" path="/v1/subscribers/{subscriberId}/credentials" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.SubscribersV1ControllerModifySubscriberChannelResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        SubscribersV1ControllerModifySubscriberChannelResponse res = sdk.subscribers().appendCredentials()
                .subscriberId("<id>")
                .body(UpdateSubscriberChannelRequestDto.builder()
                    .providerId(ChatOrPushProviderEnum.ONE_SIGNAL)
                    .credentials(ChannelCredentials.builder()
                        .webhookUrl("https://example.com/webhook")
                        .channel("general")
                        .deviceTokens(List.of(
                            "token1",
                            "token2",
                            "token3"))
                        .alertUid("12345-abcde")
                        .title("Critical Alert")
                        .imageUrl("https://example.com/image.png")
                        .state("resolved")
                        .externalUrl("https://example.com/details")
                        .build())
                    .build())
                .call();

        if (res.subscriberResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                         | Type                                                                                              | Required                                                                                          | Description                                                                                       |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| `subscriberId`                                                                                    | *String*                                                                                          | :heavy_check_mark:                                                                                | N/A                                                                                               |
| `idempotencyKey`                                                                                  | *Optional\<String>*                                                                               | :heavy_minus_sign:                                                                                | A header for idempotency purposes                                                                 |
| `body`                                                                                            | [UpdateSubscriberChannelRequestDto](../../models/components/UpdateSubscriberChannelRequestDto.md) | :heavy_check_mark:                                                                                | N/A                                                                                               |

### Response

**[SubscribersV1ControllerModifySubscriberChannelResponse](../../models/operations/SubscribersV1ControllerModifySubscriberChannelResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## markAllMessagesAs

Update subscriber's multiple in-app (inbox) notifications state such as seen, read, unseen or unread by **subscriberId**. 
      **messageId** is of type mongodbId of notifications

### Example Usage

<!-- UsageSnippet language="java" operationID="SubscribersV1Controller_markMessagesAs" method="post" path="/v1/subscribers/{subscriberId}/messages/mark-as" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.SubscribersV1ControllerMarkMessagesAsResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        SubscribersV1ControllerMarkMessagesAsResponse res = sdk.subscribers().markAllMessagesAs()
                .subscriberId("<id>")
                .body(MessageMarkAsRequestDto.builder()
                    .messageId(MessageId.of(List.of()))
                    .markAs(MessageMarkAsRequestDtoMarkAs.SEEN)
                    .build())
                .call();

        if (res.messageResponseDtos().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `subscriberId`                                                                | *String*                                                                      | :heavy_check_mark:                                                            | N/A                                                                           |
| `idempotencyKey`                                                              | *Optional\<String>*                                                           | :heavy_minus_sign:                                                            | A header for idempotency purposes                                             |
| `body`                                                                        | [MessageMarkAsRequestDto](../../models/components/MessageMarkAsRequestDto.md) | :heavy_check_mark:                                                            | N/A                                                                           |

### Response

**[SubscribersV1ControllerMarkMessagesAsResponse](../../models/operations/SubscribersV1ControllerMarkMessagesAsResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## getUnseenCount

Retrieve unseen in-app (inbox) notifications count for a subscriber by its unique key identifier **subscriberId**.

### Example Usage

<!-- UsageSnippet language="java" operationID="SubscribersV1Controller_getUnseenCount" method="get" path="/v1/subscribers/{subscriberId}/notifications/unseen" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.SubscribersV1ControllerGetUnseenCountResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        SubscribersV1ControllerGetUnseenCountResponse res = sdk.subscribers().getUnseenCount()
                .subscriberId("<id>")
                .seen(false)
                .limit(100d)
                .call();

        if (res.unseenCountResponse().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                      | Type                                           | Required                                       | Description                                    |
| ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- |
| `subscriberId`                                 | *String*                                       | :heavy_check_mark:                             | N/A                                            |
| `seen`                                         | *Optional\<Boolean>*                           | :heavy_minus_sign:                             | Indicates whether to count seen notifications. |
| `limit`                                        | *Optional\<Double>*                            | :heavy_minus_sign:                             | The maximum number of notifications to return. |
| `idempotencyKey`                               | *Optional\<String>*                            | :heavy_minus_sign:                             | A header for idempotency purposes              |

### Response

**[SubscribersV1ControllerGetUnseenCountResponse](../../models/operations/SubscribersV1ControllerGetUnseenCountResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |

## updateOnlineStatus

Update the subscriber online status by its unique key identifier **subscriberId**

### Example Usage

<!-- UsageSnippet language="java" operationID="SubscribersV1Controller_updateSubscriberOnlineFlag" method="patch" path="/v1/subscribers/{subscriberId}/online-status" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.UpdateSubscriberOnlineFlagRequestDto;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.SubscribersV1ControllerUpdateSubscriberOnlineFlagResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        SubscribersV1ControllerUpdateSubscriberOnlineFlagResponse res = sdk.subscribers().updateOnlineStatus()
                .subscriberId("<id>")
                .body(UpdateSubscriberOnlineFlagRequestDto.builder()
                    .isOnline(false)
                    .build())
                .call();

        if (res.subscriberResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                               | Type                                                                                                    | Required                                                                                                | Description                                                                                             |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `subscriberId`                                                                                          | *String*                                                                                                | :heavy_check_mark:                                                                                      | N/A                                                                                                     |
| `idempotencyKey`                                                                                        | *Optional\<String>*                                                                                     | :heavy_minus_sign:                                                                                      | A header for idempotency purposes                                                                       |
| `body`                                                                                                  | [UpdateSubscriberOnlineFlagRequestDto](../../models/components/UpdateSubscriberOnlineFlagRequestDto.md) | :heavy_check_mark:                                                                                      | N/A                                                                                                     |

### Response

**[SubscribersV1ControllerUpdateSubscriberOnlineFlagResponse](../../models/operations/SubscribersV1ControllerUpdateSubscriberOnlineFlagResponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| models/errors/ErrorDto                 | 414                                    | application/json                       |
| models/errors/ErrorDto                 | 400, 401, 403, 404, 405, 409, 413, 415 | application/json                       |
| models/errors/ValidationErrorDto       | 422                                    | application/json                       |
| models/errors/ErrorDto                 | 500                                    | application/json                       |
| models/errors/APIException             | 4XX, 5XX                               | \*/\*                                  |