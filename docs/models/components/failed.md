# Failed


## Fields

| Field                                                   | Type                                                    | Required                                                | Description                                             |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| `Error`                                                 | `string`                                                | :heavy_check_mark:                                      | Error message describing why the event failed           |
| `IdempotencyKey`                                        | `string`                                                | :heavy_check_mark:                                      | Idempotency key of the failed event for identification  |
| `Index`                                                 | `int64`                                                 | :heavy_check_mark:                                      | Index of the failed event in the original request array |