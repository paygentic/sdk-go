# MerchantReset

What the reset deletes. Every field of the chosen shape is required, so each call says what goes.


## Supported Types

### MerchantScope

```go
merchantReset := components.CreateMerchantResetMerchant(components.MerchantScope{/* values here */})
```

### CustomerScope

```go
merchantReset := components.CreateMerchantResetCustomer(components.CustomerScope{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch merchantReset.Type {
	case components.MerchantResetTypeMerchant:
		// merchantReset.MerchantScope is populated
	case components.MerchantResetTypeCustomer:
		// merchantReset.CustomerScope is populated
}
```
