# PaymentSession


## Fields

| Field                                                                        | Type                                                                         | Required                                                                     | Description                                                                  |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `URL`                                                                        | `string`                                                                     | :heavy_check_mark:                                                           | The Stripe checkout URL for the customer to complete payment.                |
| `ExpiresAt`                                                                  | optionalnullable.OptionalNullable[[time.Time](https://pkg.go.dev/time#Time)] | :heavy_minus_sign:                                                           | When the payment session expires.                                            |
| `Amount`                                                                     | `*float64`                                                                   | :heavy_minus_sign:                                                           | The payment amount in the currency's minor unit (e.g., cents).               |