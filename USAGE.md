<!-- Start SDK Example Usage [usage] -->
### Create a customer

Create a customer for each organization you bill. This is the first step in the billing setup — see the [Quickstart](https://docs.paygentic.io/getting-started/quickstart) for the full flow.

```go
package main

import (
	"context"
	paygentic "github.com/paygentic/sdk-go"
	"github.com/paygentic/sdk-go/models/components"
	"github.com/paygentic/sdk-go/models/operations"
	"log"
	"os"
)

func main() {
	ctx := context.Background()

	s := paygentic.New(
		paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
	)

	res, err := s.Customers.Create(ctx, operations.CreateCustomerRequest{
		Consumer: &operations.Consumer{
			Name:  "Jane Smith",
			Email: "jane@example.com",
			Address: components.Address{
				City:    paygentic.Pointer("San Francisco"),
				State:   paygentic.Pointer("CA"),
				Country: paygentic.Pointer("US"),
			},
		},
		MerchantID: "org_YS8jkP59V71TdUvj",
	})
	if err != nil {
		log.Fatal(err)
	}
	if res != nil {
		// handle response
	}
}

```

### Create a subscription

Subscribe a customer to a plan. If the plan includes in-advance charges, Paygentic generates an initial invoice and the subscription activates once paid.

```go
package main

import (
	"context"
	paygentic "github.com/paygentic/sdk-go"
	"github.com/paygentic/sdk-go/models/components"
	"github.com/paygentic/sdk-go/models/operations"
	"github.com/paygentic/sdk-go/types"
	"log"
	"os"
)

func main() {
	ctx := context.Background()

	s := paygentic.New(
		paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
	)

	res, err := s.Subscriptions.Create(ctx, operations.CreateSubscriptionRequest{
		CustomerID: paygentic.Pointer("cus_abc123"),
		Name:       "Monthly API Service",
		PlanID:     "plan_abc123",
		StartedAt:  types.MustTimeFromString("2024-01-15T00:00:00Z"),
	})
	if err != nil {
		log.Fatal(err)
	}
	if res != nil {
		switch res.Payment.Type {
		case components.PaymentUnionTypePending:
			// res.Payment.PaymentPending is populated
		case components.PaymentUnionTypePaid:
			// res.Payment.PaymentPaid is populated
		case components.PaymentUnionTypeAwaitingApproval:
			// res.Payment.PaymentAwaitingApproval is populated
		default:
			// Unknown type - use res.Payment.GetUnknownRaw() for raw JSON
		}

	}
}

```

### Report usage

Send meter events to record consumption once a subscription is active. The endpoint is fire-and-forget — it always returns `202 Accepted`.

```go
package main

import (
	"context"
	paygentic "github.com/paygentic/sdk-go"
	"github.com/paygentic/sdk-go/models/operations"
	"log"
	"os"
)

func main() {
	ctx := context.Background()

	s := paygentic.New(
		paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
	)

	res, err := s.Events.Ingest(ctx, operations.IngestEventRequest{
		Type:    "ai.inference",
		Source:  "https://api.myapp.com",
		Subject: "cus_abc123",
		Data: map[string]any{
			"tokens": 1500,
			"model":  "gpt-4o",
		},
	})
	if err != nil {
		log.Fatal(err)
	}
	if res != nil {
		// handle response
	}
}

```
<!-- End SDK Example Usage [usage] -->