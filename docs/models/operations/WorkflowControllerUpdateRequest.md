# WorkflowControllerUpdateRequest


## Fields

| Field                                                             | Type                                                              | Required                                                          | Description                                                       |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `workflowId`                                                      | *String*                                                          | :heavy_check_mark:                                                | N/A                                                               |
| `idempotencyKey`                                                  | *Optional\<String>*                                               | :heavy_minus_sign:                                                | A header for idempotency purposes                                 |
| `body`                                                            | [UpdateWorkflowDto](../../models/components/UpdateWorkflowDto.md) | :heavy_check_mark:                                                | Workflow update details                                           |