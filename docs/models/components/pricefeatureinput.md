# PriceFeatureInput


## Fields

| Field                                                            | Type                                                             | Required                                                         | Description                                                      |
| ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| `FeatureID`                                                      | `string`                                                         | :heavy_check_mark:                                               | The feature to associate with this price                         |
| `EntitlementTemplate`                                            | map[string]`any`                                                 | :heavy_minus_sign:                                               | Template for entitlement values when this feature is provisioned |