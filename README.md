# Paygentic Go SDK

The official Go SDK for the [Paygentic](https://paygentic.io) billing platform.

> This README is a placeholder — Speakeasy will replace it on first generation with a full, operation-by-operation reference (matching the style of [`paygentic/sdk-node`](https://github.com/paygentic/sdk-node) and [`paygentic/sdk-python`](https://github.com/paygentic/sdk-python)).

## Install

```bash
go get github.com/paygentic/sdk-go
```

## Quick start

```go
package main

import (
	"context"
	"log"
	"os"

	"github.com/paygentic/sdk-go/paygentic"
)

func main() {
	client := paygentic.New(
		paygentic.WithServerURL("https://api.sandbox.paygentic.io"),
		paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
	)

	_, err := client.Events.Ingest(context.Background(), &paygentic.EventsIngestRequest{
		Type:    "api-call",
		Source:  "my-api-service",
		Subject: "customer_abc123",
		Data:    map[string]any{"tokens": 1500},
	})
	if err != nil {
		log.Fatal(err)
	}
}
```

Swap the server URL to `https://api.paygentic.io` when going to production. No code changes otherwise.

## License

MIT — see [LICENSE](./LICENSE).
