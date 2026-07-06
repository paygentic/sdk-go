# ListBillingSchedulesRequest


## Fields

| Field                                            | Type                                             | Required                                         | Description                                      |
| ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ |
| `OrderID`                                        | `*string`                                        | :heavy_minus_sign:                               | Filter by owning order (XOR with subscriptionId) |
| `SubscriptionID`                                 | `*string`                                        | :heavy_minus_sign:                               | Filter by owning subscription (XOR with orderId) |