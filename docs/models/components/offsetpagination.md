# OffsetPagination

Offset-based pagination response.


## Fields

| Field                                         | Type                                          | Required                                      | Description                                   |
| --------------------------------------------- | --------------------------------------------- | --------------------------------------------- | --------------------------------------------- |
| `Limit`                                       | `*int64`                                      | :heavy_minus_sign:                            | Number of items returned in the current page. |
| `Offset`                                      | `*int64`                                      | :heavy_minus_sign:                            | Number of items skipped.                      |
| `Total`                                       | `*int64`                                      | :heavy_minus_sign:                            | Total number of items available.              |