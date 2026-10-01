# EditSubscriptionIntervalsRequestUnion

The operations to apply. At least one of add, edit or remove is required.


## Supported Types

### EditSubscriptionIntervalsRequest1

```go
editSubscriptionIntervalsRequestUnion := components.CreateEditSubscriptionIntervalsRequestUnionEditSubscriptionIntervalsRequest1(components.EditSubscriptionIntervalsRequest1{/* values here */})
```

### EditSubscriptionIntervalsRequest2

```go
editSubscriptionIntervalsRequestUnion := components.CreateEditSubscriptionIntervalsRequestUnionEditSubscriptionIntervalsRequest2(components.EditSubscriptionIntervalsRequest2{/* values here */})
```

### EditSubscriptionIntervalsRequest3

```go
editSubscriptionIntervalsRequestUnion := components.CreateEditSubscriptionIntervalsRequestUnionEditSubscriptionIntervalsRequest3(components.EditSubscriptionIntervalsRequest3{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch editSubscriptionIntervalsRequestUnion.Type {
	case components.EditSubscriptionIntervalsRequestUnionTypeEditSubscriptionIntervalsRequest1:
		// editSubscriptionIntervalsRequestUnion.EditSubscriptionIntervalsRequest1 is populated
	case components.EditSubscriptionIntervalsRequestUnionTypeEditSubscriptionIntervalsRequest2:
		// editSubscriptionIntervalsRequestUnion.EditSubscriptionIntervalsRequest2 is populated
	case components.EditSubscriptionIntervalsRequestUnionTypeEditSubscriptionIntervalsRequest3:
		// editSubscriptionIntervalsRequestUnion.EditSubscriptionIntervalsRequest3 is populated
}
```
