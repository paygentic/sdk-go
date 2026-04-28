# Paygentic Go SDK

The official Go SDK for the [Paygentic](https://paygentic.io) billing platform.

```bash
go get github.com/paygentic/sdk-go
```

<!-- Start Summary [summary] -->
## Summary

Paygentic API: The Paygentic API provides billing infrastructure for usage-based and subscription monetization — customers, subscriptions, usage metering, invoicing, entitlements, and payments.

See the [Quickstart](https://docs.paygentic.io/getting-started/quickstart) to go from zero to billing in a handful of steps.
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [Paygentic Go SDK](#paygentic-go-sdk)
  * [SDK Installation](#sdk-installation)
  * [SDK Example Usage](#sdk-example-usage)
  * [Authentication](#authentication)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Retries](#retries)
  * [Error Handling](#error-handling)
  * [Server Selection](#server-selection)
  * [Custom HTTP Client](#custom-http-client)
  * [Special Types](#special-types)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

To add the SDK as a dependency to your project:
```bash
go get github.com/paygentic/sdk-go
```
<!-- End SDK Installation [installation] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

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

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security scheme globally:

| Name         | Type | Scheme      | Environment Variable    |
| ------------ | ---- | ----------- | ----------------------- |
| `BearerAuth` | http | HTTP Bearer | `PAYGENTIC_BEARER_AUTH` |

You can configure it using the `WithSecurity` option when initializing the SDK client instance. For example:
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

	res, err := s.BillableMetrics.Create(ctx, operations.CreateBillableMetricRequest{
		Aggregation: operations.CreateBillableMetricAggregationSum,
		Description: "Tracks total tokens consumed per API call.",
		MerchantID:  "org_YS8jkP59V71TdUvj",
		Name:        "Token Counter",
		ProductID:   "prod_abc123",
		Unit:        "tokens",
	})
	if err != nil {
		log.Fatal(err)
	}
	if res != nil {
		// handle response
	}
}

```
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [BillableMetrics](docs/sdks/billablemetrics/README.md)

* [Create](docs/sdks/billablemetrics/README.md#create) - Create
* [List](docs/sdks/billablemetrics/README.md#list) - List
* [Get](docs/sdks/billablemetrics/README.md#get) - Get
* [Update](docs/sdks/billablemetrics/README.md#update) - Update
* [Meter](docs/sdks/billablemetrics/README.md#meter) - Query Meter Usage
* [ListEvents](docs/sdks/billablemetrics/README.md#listevents) - List Meter Events

### [Costs](docs/sdks/costs/README.md)

* [CreateCost](docs/sdks/costs/README.md#createcost) - Create
* [ListCosts](docs/sdks/costs/README.md#listcosts) - List
* [GetCost](docs/sdks/costs/README.md#getcost) - Get
* [UpdateCost](docs/sdks/costs/README.md#updatecost) - Update
* [DeleteCost](docs/sdks/costs/README.md#deletecost) - Delete
* [GetCostSummary](docs/sdks/costs/README.md#getcostsummary) - Query Summary
* [GetCostReport](docs/sdks/costs/README.md#getcostreport) - Report

### [Customers](docs/sdks/customers/README.md)

* [List](docs/sdks/customers/README.md#list) - List by Merchant
* [Create](docs/sdks/customers/README.md#create) - Create
* [Get](docs/sdks/customers/README.md#get) - Get
* [Delete](docs/sdks/customers/README.md#delete) - Delete
* [Update](docs/sdks/customers/README.md#update) - Update

### [Entitlements](docs/sdks/entitlements/README.md)

* [List](docs/sdks/entitlements/README.md#list) - List Entitlements
* [Issue](docs/sdks/entitlements/README.md#issue) - Issue Entitlement
* [Get](docs/sdks/entitlements/README.md#get) - Get Entitlement

### [Entitlements.Grants](docs/sdks/grants/README.md)

* [List](docs/sdks/grants/README.md#list) - List Grants
* [Create](docs/sdks/grants/README.md#create) - Create Grant
* [Purchase](docs/sdks/grants/README.md#purchase) - Purchase Grant
* [Get](docs/sdks/grants/README.md#get) - Get Grant
* [Void](docs/sdks/grants/README.md#void) - Void Grant

### [Events](docs/sdks/events/README.md)

* [Ingest](docs/sdks/events/README.md#ingest) - Ingest Event

### [Features](docs/sdks/features/README.md)

* [List](docs/sdks/features/README.md#list) - List
* [Create](docs/sdks/features/README.md#create) - Create
* [Get](docs/sdks/features/README.md#get) - Get
* [Update](docs/sdks/features/README.md#update) - Update
* [Delete](docs/sdks/features/README.md#delete) - Delete

### [Fees](docs/sdks/fees/README.md)

* [Create](docs/sdks/fees/README.md#create) - Create
* [List](docs/sdks/fees/README.md#list) - List
* [Get](docs/sdks/fees/README.md#get) - Get
* [Update](docs/sdks/fees/README.md#update) - Update
* [Delete](docs/sdks/fees/README.md#delete) - Delete
* [GetPrice](docs/sdks/fees/README.md#getprice) - Get Fee Price

### [InvoicesV2](docs/sdks/invoicesv2/README.md)

* [List](docs/sdks/invoicesv2/README.md#list) - List
* [ListLineItems](docs/sdks/invoicesv2/README.md#listlineitems) - List Line Items
* [CreateLineItem](docs/sdks/invoicesv2/README.md#createlineitem) - Create Manual Line Item
* [Get](docs/sdks/invoicesv2/README.md#get) - Get
* [GetLineItems](docs/sdks/invoicesv2/README.md#getlineitems) - Get Line Items

### [Payments](docs/sdks/payments/README.md)

* [List](docs/sdks/payments/README.md#list) - List Payments
* [Create](docs/sdks/payments/README.md#create) - Create Payment
* [Get](docs/sdks/payments/README.md#get) - Get Payment

### [Plans](docs/sdks/plans/README.md)

* [Create](docs/sdks/plans/README.md#create) - Create
* [List](docs/sdks/plans/README.md#list) - List
* [ListAvailable](docs/sdks/plans/README.md#listavailable) - List Available Plans
* [Get](docs/sdks/plans/README.md#get) - Get
* [Update](docs/sdks/plans/README.md#update) - Update

### [Prices](docs/sdks/prices/README.md)

* [Create](docs/sdks/prices/README.md#create) - Create
* [List](docs/sdks/prices/README.md#list) - List
* [Get](docs/sdks/prices/README.md#get) - Get
* [Update](docs/sdks/prices/README.md#update) - Update
* [Delete](docs/sdks/prices/README.md#delete) - Delete

### [Products](docs/sdks/products/README.md)

* [Create](docs/sdks/products/README.md#create) - Create
* [List](docs/sdks/products/README.md#list) - List
* [Get](docs/sdks/products/README.md#get) - Get
* [Update](docs/sdks/products/README.md#update) - Update

### [Revenue](docs/sdks/revenue/README.md)

* [Get](docs/sdks/revenue/README.md#get) - Get revenue summary

### [Sources](docs/sdks/sources/README.md)

* [Create](docs/sdks/sources/README.md#create) - Create
* [List](docs/sdks/sources/README.md#list) - List
* [Get](docs/sdks/sources/README.md#get) - Get
* [Update](docs/sdks/sources/README.md#update) - Update

### [Sources.Events](docs/sdks/sourcesevents/README.md)

* [List](docs/sdks/sourcesevents/README.md#list) - List Events
* [Approve](docs/sdks/sourcesevents/README.md#approve) - Approve
* [Reject](docs/sdks/sourcesevents/README.md#reject) - Reject
* [BulkApprove](docs/sdks/sourcesevents/README.md#bulkapprove) - Bulk Approve
* [BulkReject](docs/sdks/sourcesevents/README.md#bulkreject) - Bulk Reject

### [Sources.Rules](docs/sdks/rules/README.md)

* [List](docs/sdks/rules/README.md#list) - List Rules
* [Create](docs/sdks/rules/README.md#create) - Create Rule
* [Get](docs/sdks/rules/README.md#get) - Get Rule
* [Update](docs/sdks/rules/README.md#update) - Update Rule
* [Delete](docs/sdks/rules/README.md#delete) - Delete Rule

### [Subscriptions](docs/sdks/subscriptions/README.md)

* [List](docs/sdks/subscriptions/README.md#list) - List
* [Create](docs/sdks/subscriptions/README.md#create) - Create
* [Get](docs/sdks/subscriptions/README.md#get) - Get
* [GeneratePortalLink](docs/sdks/subscriptions/README.md#generateportallink) - Generate Portal Link
* [Terminate](docs/sdks/subscriptions/README.md#terminate) - Terminate

### [TestClocks](docs/sdks/testclocks/README.md)

* [List](docs/sdks/testclocks/README.md#list) - List
* [Create](docs/sdks/testclocks/README.md#create) - Create
* [Get](docs/sdks/testclocks/README.md#get) - Get
* [Advance](docs/sdks/testclocks/README.md#advance) - Advance
* [Delete](docs/sdks/testclocks/README.md#delete) - Delete

### [Users](docs/sdks/users/README.md)

* [Get](docs/sdks/users/README.md#get) - Get
* [Update](docs/sdks/users/README.md#update) - Update

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Retries [retries] -->
## Retries

Some of the endpoints in this SDK support retries. If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API. However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply provide a `retry.Config` object to the call by using the `WithRetries` option:
```go
package main

import (
	"context"
	paygentic "github.com/paygentic/sdk-go"
	"github.com/paygentic/sdk-go/models/operations"
	"github.com/paygentic/sdk-go/retry"
	"log"
	"models/operations"
	"os"
)

func main() {
	ctx := context.Background()

	s := paygentic.New(
		paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
	)

	res, err := s.BillableMetrics.Create(ctx, operations.CreateBillableMetricRequest{
		Aggregation: operations.CreateBillableMetricAggregationSum,
		Description: "Tracks total tokens consumed per API call.",
		MerchantID:  "org_YS8jkP59V71TdUvj",
		Name:        "Token Counter",
		ProductID:   "prod_abc123",
		Unit:        "tokens",
	}, operations.WithRetries(
		retry.Config{
			Strategy: "backoff",
			Backoff: &retry.BackoffStrategy{
				InitialInterval: 1,
				MaxInterval:     50,
				Exponent:        1.1,
				MaxElapsedTime:  100,
			},
			RetryConnectionErrors: false,
		}))
	if err != nil {
		log.Fatal(err)
	}
	if res != nil {
		// handle response
	}
}

```

If you'd like to override the default retry strategy for all operations that support retries, you can use the `WithRetryConfig` option at SDK initialization:
```go
package main

import (
	"context"
	paygentic "github.com/paygentic/sdk-go"
	"github.com/paygentic/sdk-go/models/operations"
	"github.com/paygentic/sdk-go/retry"
	"log"
	"os"
)

func main() {
	ctx := context.Background()

	s := paygentic.New(
		paygentic.WithRetryConfig(
			retry.Config{
				Strategy: "backoff",
				Backoff: &retry.BackoffStrategy{
					InitialInterval: 1,
					MaxInterval:     50,
					Exponent:        1.1,
					MaxElapsedTime:  100,
				},
				RetryConnectionErrors: false,
			}),
		paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
	)

	res, err := s.BillableMetrics.Create(ctx, operations.CreateBillableMetricRequest{
		Aggregation: operations.CreateBillableMetricAggregationSum,
		Description: "Tracks total tokens consumed per API call.",
		MerchantID:  "org_YS8jkP59V71TdUvj",
		Name:        "Token Counter",
		ProductID:   "prod_abc123",
		Unit:        "tokens",
	})
	if err != nil {
		log.Fatal(err)
	}
	if res != nil {
		// handle response
	}
}

```
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

Handling errors in this SDK should largely match your expectations. All operations return a response object or an error, they will never return both.

By Default, an API error will return `errors.PaygenticDefaultError`. When custom error responses are specified for an operation, the SDK may also return their associated error. You can refer to respective *Errors* tables in SDK docs for more details on possible error types for each operation.

For example, the `Create` function may return the following errors:

| Error Type                   | Status Code | Content Type     |
| ---------------------------- | ----------- | ---------------- |
| errors.BadRequest            | 400         | application/json |
| errors.Error                 | 401, 403    | application/json |
| errors.Error                 | 500         | application/json |
| errors.PaygenticDefaultError | 4XX, 5XX    | \*/\*            |

### Example

```go
package main

import (
	"context"
	"errors"
	paygentic "github.com/paygentic/sdk-go"
	"github.com/paygentic/sdk-go/models/errors"
	"github.com/paygentic/sdk-go/models/operations"
	"log"
	"os"
)

func main() {
	ctx := context.Background()

	s := paygentic.New(
		paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
	)

	res, err := s.BillableMetrics.Create(ctx, operations.CreateBillableMetricRequest{
		Aggregation: operations.CreateBillableMetricAggregationSum,
		Description: "Tracks total tokens consumed per API call.",
		MerchantID:  "org_YS8jkP59V71TdUvj",
		Name:        "Token Counter",
		ProductID:   "prod_abc123",
		Unit:        "tokens",
	})
	if err != nil {

		var e *errors.BadRequest
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}

		var e *errors.Error
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}

		var e *errors.Error
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}

		var e *errors.PaygenticDefaultError
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}
	}
}

```
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Select Server by Index

You can override the default server globally using the `WithServerIndex(serverIndex int)` option when initializing the SDK client instance. The selected server will then be used as the default on the operations that use it. This table lists the indexes associated with the available servers:

| #   | Server                             | Description    |
| --- | ---------------------------------- | -------------- |
| 0   | `https://api.paygentic.io`         | Production API |
| 1   | `https://api.sandbox.paygentic.io` | Sandbox API    |

#### Example

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
		paygentic.WithServerIndex(0),
		paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
	)

	res, err := s.BillableMetrics.Create(ctx, operations.CreateBillableMetricRequest{
		Aggregation: operations.CreateBillableMetricAggregationSum,
		Description: "Tracks total tokens consumed per API call.",
		MerchantID:  "org_YS8jkP59V71TdUvj",
		Name:        "Token Counter",
		ProductID:   "prod_abc123",
		Unit:        "tokens",
	})
	if err != nil {
		log.Fatal(err)
	}
	if res != nil {
		// handle response
	}
}

```

### Override Server URL Per-Client

The default server can also be overridden globally using the `WithServerURL(serverURL string)` option when initializing the SDK client instance. For example:
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
		paygentic.WithServerURL("https://api.sandbox.paygentic.io"),
		paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
	)

	res, err := s.BillableMetrics.Create(ctx, operations.CreateBillableMetricRequest{
		Aggregation: operations.CreateBillableMetricAggregationSum,
		Description: "Tracks total tokens consumed per API call.",
		MerchantID:  "org_YS8jkP59V71TdUvj",
		Name:        "Token Counter",
		ProductID:   "prod_abc123",
		Unit:        "tokens",
	})
	if err != nil {
		log.Fatal(err)
	}
	if res != nil {
		// handle response
	}
}

```
<!-- End Server Selection [server] -->

<!-- Start Custom HTTP Client [http-client] -->
## Custom HTTP Client

The Go SDK makes API calls that wrap an internal HTTP client. The requirements for the HTTP client are very simple. It must match this interface:

```go
type HTTPClient interface {
	Do(req *http.Request) (*http.Response, error)
}
```

The built-in `net/http` client satisfies this interface and a default client based on the built-in is provided by default. To replace this default with a client of your own, you can implement this interface yourself or provide your own client configured as desired. Here's a simple example, which adds a client with a 30 second timeout.

```go
import (
	"net/http"
	"time"

	"github.com/paygentic/sdk-go"
)

var (
	httpClient = &http.Client{Timeout: 30 * time.Second}
	sdkClient  = paygentic.New(paygentic.WithClient(httpClient))
)
```

This can be a convenient way to configure timeouts, cookies, proxies, custom headers, and other low-level configuration.
<!-- End Custom HTTP Client [http-client] -->

<!-- Start Special Types [types] -->
## Special Types

This SDK defines the following custom types to assist with marshalling and unmarshalling data.

### Date

`types.Date` is a wrapper around time.Time that allows for JSON marshaling a date string formatted as "2006-01-02".

#### Usage

```go
d1 := types.NewDate(time.Now()) // returns *types.Date

d2 := types.DateFromTime(time.Now()) // returns types.Date

d3, err := types.NewDateFromString("2019-01-01") // returns *types.Date, error

d4, err := types.DateFromString("2019-01-01") // returns types.Date, error

d5 := types.MustNewDateFromString("2019-01-01") // returns *types.Date and panics on error

d6 := types.MustDateFromString("2019-01-01") // returns types.Date and panics on error
```
<!-- End Special Types [types] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->
