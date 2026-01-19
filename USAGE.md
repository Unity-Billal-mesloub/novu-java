<!-- Start SDK Example Usage [usage] -->
### Trigger Notification Event

```java
package hello.world;

import java.lang.Exception;
import java.util.Map;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.EventsControllerTriggerResponse;

public class Application {

    public static void main(String[] args) throws PayloadValidationExceptionDto, ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        EventsControllerTriggerResponse res = sdk.trigger()
                .body(TriggerEventRequestDto.builder()
                    .workflowId("workflow_identifier")
                    .to(To2.of("SUBSCRIBER_ID"))
                    .payload(Map.ofEntries(
                        Map.entry("comment_id", "string"),
                        Map.entry("post", Map.ofEntries(
                            Map.entry("text", "string")))))
                    .overrides(TriggerEventRequestDtoOverrides.builder()
                        .build())
                    .actor(TriggerEventRequestDtoActor.of("<value>"))
                    .context(Map.ofEntries(
                        Map.entry("key", TriggerEventRequestDtoContextUnion.of("org-acme"))))
                    .build())
                .call();

        if (res.triggerEventResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Cancel Triggered Event

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.errors.ErrorDto;
import org.openapis.openapi.models.errors.ValidationErrorDto;
import org.openapis.openapi.models.operations.EventsControllerCancelResponse;

public class Application {

    public static void main(String[] args) throws ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        EventsControllerCancelResponse res = sdk.cancel()
                .transactionId("<id>")
                .call();

        if (res.boolean_().isPresent()) {
            // handle response
        }
    }
}
```

### Broadcast Event to All

```java
package hello.world;

import java.lang.Exception;
import java.util.Map;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.EventsControllerBroadcastEventToAllResponse;

public class Application {

    public static void main(String[] args) throws PayloadValidationExceptionDto, ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        EventsControllerBroadcastEventToAllResponse res = sdk.triggerBroadcast()
                .body(TriggerEventToAllRequestDto.builder()
                    .name("<value>")
                    .payload(Map.ofEntries(
                        Map.entry("comment_id", "string"),
                        Map.entry("post", Map.ofEntries(
                            Map.entry("text", "string")))))
                    .overrides(TriggerEventToAllRequestDtoOverrides.builder()
                        .additionalProperties(Map.ofEntries(
                            Map.entry("fcm", Map.ofEntries(
                                Map.entry("data", Map.ofEntries(
                                    Map.entry("key", "value")))))))
                        .build())
                    .actor(TriggerEventToAllRequestDtoActor.of(SubscriberPayloadDto.builder()
                        .subscriberId("<id>")
                        .firstName("John")
                        .lastName("Doe")
                        .email("john.doe@example.com")
                        .phone("+1234567890")
                        .avatar("https://example.com/avatar.jpg")
                        .locale("en-US")
                        .timezone("America/New_York")
                        .build()))
                    .context(Map.ofEntries(
                        Map.entry("key", TriggerEventToAllRequestDtoContextUnion.of("org-acme"))))
                    .build())
                .call();

        if (res.triggerEventResponseDto().isPresent()) {
            // handle response
        }
    }
}
```

### Trigger Notification Events in Bulk

```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import java.util.Map;
import org.openapis.openapi.Novu;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.EventsControllerTriggerBulkResponse;

public class Application {

    public static void main(String[] args) throws PayloadValidationExceptionDto, ErrorDto, ValidationErrorDto, Exception {

        Novu sdk = Novu.builder()
                .secretKey("YOUR_SECRET_KEY_HERE")
            .build();

        EventsControllerTriggerBulkResponse res = sdk.triggerBulk()
                .body(BulkTriggerEventDto.builder()
                    .events(List.of(
                        TriggerEventRequestDto.builder()
                            .workflowId("workflow_identifier")
                            .to(To2.of("SUBSCRIBER_ID"))
                            .payload(Map.ofEntries(
                                Map.entry("comment_id", "string"),
                                Map.entry("post", Map.ofEntries(
                                    Map.entry("text", "string")))))
                            .overrides(TriggerEventRequestDtoOverrides.builder()
                                .build())
                            .actor(TriggerEventRequestDtoActor.of(SubscriberPayloadDto.builder()
                                .subscriberId("<id>")
                                .firstName("John")
                                .lastName("Doe")
                                .email("john.doe@example.com")
                                .phone("+1234567890")
                                .avatar("https://example.com/avatar.jpg")
                                .locale("en-US")
                                .timezone("America/New_York")
                                .build()))
                            .context(Map.ofEntries(
                                Map.entry("key", TriggerEventRequestDtoContextUnion.of("org-acme"))))
                            .build()))
                    .build())
                .call();

        if (res.triggerEventResponseDtos().isPresent()) {
            // handle response
        }
    }
}
```
<!-- End SDK Example Usage [usage] -->