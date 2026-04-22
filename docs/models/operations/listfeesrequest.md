# ListFeesRequest


## Fields

| Field                                    | Type                                     | Required                                 | Description                              |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| `Limit`                                  | `*int64`                                 | :heavy_minus_sign:                       | Number of fees to return.                |
| `MerchantID`                             | `string`                                 | :heavy_check_mark:                       | Filter fees by merchant organization ID. |
| `Offset`                                 | `*int64`                                 | :heavy_minus_sign:                       | Number of fees to skip.                  |
| `ProductID`                              | `*string`                                | :heavy_minus_sign:                       | Filter fees by product ID.               |