# OutOfBandPaymentResult


## Fields

| Field                                                    | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `Method`                                                 | `string`                                                 | :heavy_check_mark:                                       | Discriminator: an out-of-band payment was recorded.      |
| `Invoice`                                                | [components.Invoice](../../models/components/invoice.md) | :heavy_check_mark:                                       | N/A                                                      |