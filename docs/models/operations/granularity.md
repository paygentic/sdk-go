# Granularity

Roll the ledger up into calendar-aligned buckets (UTC) instead of itemized entries. Calendar periods with no activity are omitted from the response. To see the individual entries behind a bucket, request the itemized ledger (omit `granularity`) with the same `entryType` filter and `from`/`to` narrowed to that bucket's `period`.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/operations"
)

value := operations.GranularityHour
```


## Values

| Name               | Value              |
| ------------------ | ------------------ |
| `GranularityHour`  | hour               |
| `GranularityDay`   | day                |
| `GranularityMonth` | month              |