# PdfSource

Who produced the document at pdfUrl, or null when there is none. `paygentic` means pdfUrl is this API's download endpoint and the request must carry your API key; `tax_provider` means it is the provider's own link, which opens directly in a browser.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.PdfSourcePaygentic

// Open enum: custom values can be created with a direct type cast
custom := components.PdfSource("custom_value")
```


## Values

| Name                   | Value                  |
| ---------------------- | ---------------------- |
| `PdfSourcePaygentic`   | paygentic              |
| `PdfSourceTaxProvider` | tax_provider           |