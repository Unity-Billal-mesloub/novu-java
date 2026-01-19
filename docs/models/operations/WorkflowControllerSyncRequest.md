# WorkflowControllerSyncRequest


## Fields

| Field                                                         | Type                                                          | Required                                                      | Description                                                   |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| `workflowId`                                                  | *String*                                                      | :heavy_check_mark:                                            | N/A                                                           |
| `idempotencyKey`                                              | *Optional\<String>*                                           | :heavy_minus_sign:                                            | A header for idempotency purposes                             |
| `body`                                                        | [SyncWorkflowDto](../../models/components/SyncWorkflowDto.md) | :heavy_check_mark:                                            | Sync workflow details                                         |