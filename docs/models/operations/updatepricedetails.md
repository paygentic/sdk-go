# UpdatePriceDetails


## Fields

| Field                                                               | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `PriceID`                                                           | `*string`                                                           | :heavy_minus_sign:                                                  | N/A                                                                 |
| `Fields`                                                            | []`string`                                                          | :heavy_minus_sign:                                                  | N/A                                                                 |
| `SubscriptionCount`                                                 | `*int64`                                                            | :heavy_minus_sign:                                                  | N/A                                                                 |
| `SubscriptionProposalIds`                                           | []`string`                                                          | :heavy_minus_sign:                                                  | Up to ten of the pending subscription proposals that name the price |
| `SubscriptionProposalCount`                                         | `*int64`                                                            | :heavy_minus_sign:                                                  | How many pending subscription proposals name the price              |