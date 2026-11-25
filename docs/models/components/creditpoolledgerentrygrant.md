# CreditPoolLedgerEntryGrant

The grant this entry relates to — the grant that funded the pool for `increment`, or the grant whose balance changed for `decrement`, `void`, and `expiration`.


## Fields

| Field                                                                        | Type                                                                         | Required                                                                     | Description                                                                  |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `ID`                                                                         | `string`                                                                     | :heavy_check_mark:                                                           | N/A                                                                          |
| `ExpiresAt`                                                                  | [*time.Time](https://pkg.go.dev/time#Time)                                   | :heavy_check_mark:                                                           | The grant's own expiry, or null if it never expires.                         |
| `ConversionRate`                                                             | `string`                                                                     | :heavy_check_mark:                                                           | The pool's pricing-unit conversion rate ($ per credit), as a decimal string. |