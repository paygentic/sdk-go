# Timing

When the migration takes effect. `next_period` moves everything at the end of the current billing period. `immediate` changes entitlements at once, bills in-arrears prices for the whole current period at the target version, and changes in-advance prices at the end of the current period. Neither prorates. If absent, the plan's versionTransition applies.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.TimingNextPeriod
```


## Values

| Name               | Value              |
| ------------------ | ------------------ |
| `TimingNextPeriod` | next_period        |
| `TimingImmediate`  | immediate          |