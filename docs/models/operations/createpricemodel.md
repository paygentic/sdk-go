# CreatePriceModel

Pricing calculation model. Required for billable metrics, optional for fees (defaults to 'standard').

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/operations"
)

value := operations.CreatePriceModelStandard
```


## Values

| Name                         | Value                        |
| ---------------------------- | ---------------------------- |
| `CreatePriceModelStandard`   | standard                     |
| `CreatePriceModelDynamic`    | dynamic                      |
| `CreatePriceModelVolume`     | volume                       |
| `CreatePriceModelPercentage` | percentage                   |