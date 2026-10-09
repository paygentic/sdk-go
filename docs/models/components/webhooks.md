# Webhooks


## Fields

| Field                                                                  | Type                                                                   | Required                                                               | Description                                                            |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `Object`                                                               | [components.WebhooksObject](../../models/components/webhooksobject.md) | :heavy_check_mark:                                                     | Object type identifier                                                 |
| `ApplicationID`                                                        | `string`                                                               | :heavy_check_mark:                                                     | Svix application identifier                                            |
| `CreatedAt`                                                            | [time.Time](https://pkg.go.dev/time#Time)                              | :heavy_check_mark:                                                     | When webhooks were first enabled                                       |
| `Enabled`                                                              | `bool`                                                                 | :heavy_check_mark:                                                     | Whether webhooks are enabled                                           |
| `MerchantID`                                                           | `string`                                                               | :heavy_check_mark:                                                     | Merchant identifier                                                    |
| `UpdatedAt`                                                            | [time.Time](https://pkg.go.dev/time#Time)                              | :heavy_check_mark:                                                     | When webhooks were last updated                                        |