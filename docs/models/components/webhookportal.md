# WebhookPortal


## Fields

| Field                                                                            | Type                                                                             | Required                                                                         | Description                                                                      |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `Object`                                                                         | [components.WebhookPortalObject](../../models/components/webhookportalobject.md) | :heavy_check_mark:                                                               | Object type identifier                                                           |
| `ExpiresAt`                                                                      | [time.Time](https://pkg.go.dev/time#Time)                                        | :heavy_check_mark:                                                               | When the portal link expires                                                     |
| `URL`                                                                            | `string`                                                                         | :heavy_check_mark:                                                               | Magic link URL to access the webhook portal                                      |