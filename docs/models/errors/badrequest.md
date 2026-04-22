# BadRequest

Bad Request - The request could not be understood or was missing required parameters


## Supported Types

### Error

```go
badRequest := errors.CreateBadRequestError(errors.Error{/* values here */})
```

### ValidationError

```go
badRequest := errors.CreateBadRequestValidationError(errors.ValidationError{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch badRequest.Type {
	case errors.BadRequestTypeError:
		// badRequest.Error_ is populated
	case errors.BadRequestTypeValidationError:
		// badRequest.ValidationError is populated
	default:
		// Unknown type - use badRequest.GetUnknownRaw() for raw JSON
}
```
