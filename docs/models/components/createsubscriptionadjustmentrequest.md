# CreateSubscriptionAdjustmentRequest

One adjustment to attach to the subscription. The type decides which number the body carries: a rate for percentageDiscount, a unit count and one target price for usageDiscount.


## Supported Types

### CreatePercentageDiscountAdjustment

```go
createSubscriptionAdjustmentRequest := components.CreateCreateSubscriptionAdjustmentRequestPercentageDiscount(components.CreatePercentageDiscountAdjustment{/* values here */})
```

### CreateUsageDiscountAdjustment

```go
createSubscriptionAdjustmentRequest := components.CreateCreateSubscriptionAdjustmentRequestUsageDiscount(components.CreateUsageDiscountAdjustment{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch createSubscriptionAdjustmentRequest.Type {
	case components.CreateSubscriptionAdjustmentRequestTypePercentageDiscount:
		// createSubscriptionAdjustmentRequest.CreatePercentageDiscountAdjustment is populated
	case components.CreateSubscriptionAdjustmentRequestTypeUsageDiscount:
		// createSubscriptionAdjustmentRequest.CreateUsageDiscountAdjustment is populated
}
```
