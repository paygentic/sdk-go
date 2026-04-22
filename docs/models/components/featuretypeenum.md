# FeatureTypeEnum

The type of feature: `boolean` (on/off), `static` (with config), or `metered` (usage-based).

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.FeatureTypeEnumBoolean

// Open enum: custom values can be created with a direct type cast
custom := components.FeatureTypeEnum("custom_value")
```


## Values

| Name                     | Value                    |
| ------------------------ | ------------------------ |
| `FeatureTypeEnumBoolean` | boolean                  |
| `FeatureTypeEnumStatic`  | static                   |
| `FeatureTypeEnumMetered` | metered                  |