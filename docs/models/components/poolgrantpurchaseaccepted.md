# PoolGrantPurchaseAccepted


## Fields

| Field                                                                              | Type                                                                               | Required                                                                           | Description                                                                        |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `Processing`                                                                       | `bool`                                                                             | :heavy_check_mark:                                                                 | True while the invoice's settlement is still in progress.                          |
| `InvoiceID`                                                                        | `string`                                                                           | :heavy_check_mark:                                                                 | The invoice ID the caller can poll or retry against with the same idempotency key. |