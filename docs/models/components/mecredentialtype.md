# MeCredentialType

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.MeCredentialTypeSession

// Open enum: custom values can be created with a direct type cast
custom := components.MeCredentialType("custom_value")
```


## Values

| Name                      | Value                     |
| ------------------------- | ------------------------- |
| `MeCredentialTypeSession` | session                   |
| `MeCredentialTypeAPIKey`  | apiKey                    |
| `MeCredentialTypeOauth`   | oauth                     |
| `MeCredentialTypeSystem`  | system                    |