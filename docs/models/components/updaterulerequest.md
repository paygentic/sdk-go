# UpdateRuleRequest


## Fields

| Field                                                                  | Type                                                                   | Required                                                               | Description                                                            |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `Conditions`                                                           | [][components.RuleCondition](../../models/components/rulecondition.md) | :heavy_minus_sign:                                                     | List of conditions that must ALL be met (AND logic)                    |
| `Description`                                                          | `*string`                                                              | :heavy_minus_sign:                                                     | Detailed description of what this source rule does                     |
| `Enabled`                                                              | `*bool`                                                                | :heavy_minus_sign:                                                     | Whether this rule should be active                                     |
| `Name`                                                                 | `*string`                                                              | :heavy_minus_sign:                                                     | Human-readable name for the source rule                                |
| `Order`                                                                | `*int64`                                                               | :heavy_minus_sign:                                                     | Priority order for rule evaluation (lower numbers are evaluated first) |