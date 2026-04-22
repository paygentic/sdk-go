# CreateGrantRequest


## Fields

| Field                                                                        | Type                                                                         | Required                                                                     | Description                                                                  |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `Amount`                                                                     | `float64`                                                                    | :heavy_check_mark:                                                           | The number of credits to grant.                                              |
| `EffectiveAt`                                                                | [*time.Time](https://pkg.go.dev/time#Time)                                   | :heavy_minus_sign:                                                           | When the grant becomes effective. Defaults to now.                           |
| `ExpiresAt`                                                                  | optionalnullable.OptionalNullable[[time.Time](https://pkg.go.dev/time#Time)] | :heavy_minus_sign:                                                           | When the grant expires. If omitted, the grant does not expire.               |
| `IdempotencyKey`                                                             | `string`                                                                     | :heavy_check_mark:                                                           | Idempotency key to prevent duplicate grants. Must be unique per entitlement. |