# SubscriptionCustomer

Customer details with merchant and consumer information. Only included when include=customer is specified in the list query.


## Fields

| Field                                                       | Type                                                        | Required                                                    | Description                                                 |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| `ID`                                                        | `*string`                                                   | :heavy_minus_sign:                                          | Customer ID                                                 |
| `MerchantID`                                                | `*string`                                                   | :heavy_minus_sign:                                          | Merchant organization ID                                    |
| `Merchant`                                                  | [*components.Merchant](../../models/components/merchant.md) | :heavy_minus_sign:                                          | N/A                                                         |
| `Consumer`                                                  | [*components.Consumer](../../models/components/consumer.md) | :heavy_minus_sign:                                          | N/A                                                         |