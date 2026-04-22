# RuleCondition

A single condition that must be met for a rule to trigger auto-acceptance. Multiple conditions in a rule use AND logic.


## Fields

| Field                                                                        | Type                                                                         | Required                                                                     | Description                                                                  |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `Operator`                                                                   | [components.Operator](../../models/components/operator.md)                   | :heavy_check_mark:                                                           | The comparison operator to use                                               |
| `Type`                                                                       | [components.RuleConditionType](../../models/components/ruleconditiontype.md) | :heavy_check_mark:                                                           | The type of field to evaluate                                                |
| `Value`                                                                      | [components.ValueUnion](../../models/components/valueunion.md)               | :heavy_check_mark:                                                           | The value to compare against                                                 |