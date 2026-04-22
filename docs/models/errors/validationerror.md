# ValidationError


## Fields

| Field                                                         | Type                                                          | Required                                                      | Description                                                   |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| `Error`                                                       | [*components.ErrorEnum](../../models/components/errorenum.md) | :heavy_minus_sign:                                            | Error type indicating validation failure                      |
| `Message`                                                     | `string`                                                      | :heavy_check_mark:                                            | Human-readable error message                                  |
| `Errors`                                                      | [][components.Error](../../models/components/error.md)        | :heavy_check_mark:                                            | Array of field-specific validation errors                     |