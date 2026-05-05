# OffsetPagination

Offset-based pagination response.


## Fields

| Field                            | Type                             | Required                         | Description                      |
| -------------------------------- | -------------------------------- | -------------------------------- | -------------------------------- |
| `Limit`                          | `int64`                          | :heavy_check_mark:               | Requested page size.             |
| `Offset`                         | `int64`                          | :heavy_check_mark:               | Number of items skipped.         |
| `Total`                          | `int64`                          | :heavy_check_mark:               | Total number of items available. |