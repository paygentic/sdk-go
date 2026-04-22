# Address

Address is required for tax calculation. Must include: country (ISO 3166-1 alpha-2) and zipCode. The state/region field is required and validated for US/CA addresses only (custom validation in API logic). Postal code format is not validated but will be normalized.


## Fields

| Field                             | Type                              | Required                          | Description                       |
| --------------------------------- | --------------------------------- | --------------------------------- | --------------------------------- |
| `Line1`                           | `*string`                         | :heavy_minus_sign:                | N/A                               |
| `Line2`                           | `*string`                         | :heavy_minus_sign:                | N/A                               |
| `City`                            | `*string`                         | :heavy_minus_sign:                | N/A                               |
| `State`                           | `*string`                         | :heavy_minus_sign:                | N/A                               |
| `Country`                         | `string`                          | :heavy_check_mark:                | 2 character ISO 3166 country code |
| `ZipCode`                         | `string`                          | :heavy_check_mark:                | N/A                               |