# PaymentAwaitingApproval

Invoice 0 awaiting merchant approval before payment can proceed. The invoice is in DRAFT status with totals calculated. Approval is a platform-managed action and will be available via a public endpoint in a future release.


## Fields

| Field                                         | Type                                          | Required                                      | Description                                   |
| --------------------------------------------- | --------------------------------------------- | --------------------------------------------- | --------------------------------------------- |
| `InvoiceID`                                   | `string`                                      | :heavy_check_mark:                            | The Invoice 0 id awaiting approval            |
| `Amount`                                      | `string`                                      | :heavy_check_mark:                            | Total payment amount in decimal dollar format |
| `Status`                                      | `string`                                      | :heavy_check_mark:                            | Payment status                                |