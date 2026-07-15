# IngestEventRequest


## Supported Types

### IngestEventRequestBody1

```go
ingestEventRequest := operations.CreateIngestEventRequestIngestEventRequestBody1(operations.IngestEventRequestBody1{/* values here */})
```

### IngestEventRequestBody2

```go
ingestEventRequest := operations.CreateIngestEventRequestIngestEventRequestBody2(operations.IngestEventRequestBody2{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch ingestEventRequest.Type {
	case operations.IngestEventRequestTypeIngestEventRequestBody1:
		// ingestEventRequest.IngestEventRequestBody1 is populated
	case operations.IngestEventRequestTypeIngestEventRequestBody2:
		// ingestEventRequest.IngestEventRequestBody2 is populated
}
```
