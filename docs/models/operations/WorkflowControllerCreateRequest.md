# WorkflowControllerCreateRequest


## Fields

| Field                                                             | Type                                                              | Required                                                          | Description                                                       |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `idempotencyKey`                                                  | *Optional\<String>*                                               | :heavy_minus_sign:                                                | A header for idempotency purposes                                 |
| `body`                                                            | [CreateWorkflowDto](../../models/components/CreateWorkflowDto.md) | :heavy_check_mark:                                                | Workflow creation details                                         |