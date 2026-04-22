# Subscriptions

## Overview

A `Subscription` is a customer's commitment to purchase a `Product` following the terms of a `Plan` and its linked `Prices`.

### Available Operations

* [List](#list) - List
* [Create](#create) - Create
* [Get](#get) - Get
* [GeneratePortalLink](#generateportallink) - Generate Portal Link
* [Terminate](#terminate) - Terminate

## List

List

### Example Usage

<!-- UsageSnippet language="go" operationID="listSubscriptions" method="get" path="/v0/subscriptions" -->
```go
package main

import(
	"context"
	"os"
	paygentic "github.com/paygentic/sdk-go"
	"github.com/paygentic/sdk-go/models/operations"
	"log"
)

func main() {
    ctx := context.Background()

    s := paygentic.New(
        paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
    )

    res, err := s.Subscriptions.List(ctx, &operations.ListSubscriptionsRequest{})
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                  | Type                                                                                       | Required                                                                                   | Description                                                                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `ctx`                                                                                      | [context.Context](https://pkg.go.dev/context#Context)                                      | :heavy_check_mark:                                                                         | The context to use for the request.                                                        |
| `request`                                                                                  | [operations.ListSubscriptionsRequest](../../models/operations/listsubscriptionsrequest.md) | :heavy_check_mark:                                                                         | The request object to use for the request.                                                 |
| `opts`                                                                                     | [][operations.Option](../../models/operations/option.md)                                   | :heavy_minus_sign:                                                                         | The options for this request.                                                              |

### Response

**[*operations.ListSubscriptionsResponse](../../models/operations/listsubscriptionsresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## Create

Creates a subscription for an existing customer or creates a new customer as part of the action.

### Example Usage

<!-- UsageSnippet language="go" operationID="createSubscription" method="post" path="/v0/subscriptions" -->
```go
package main

import(
	"context"
	"os"
	paygentic "github.com/paygentic/sdk-go"
	"github.com/paygentic/sdk-go/types"
	"github.com/paygentic/sdk-go/models/operations"
	"log"
	"github.com/paygentic/sdk-go/models/components"
)

func main() {
    ctx := context.Background()

    s := paygentic.New(
        paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
    )

    res, err := s.Subscriptions.Create(ctx, operations.CreateSubscriptionRequest{
        CustomerID: paygentic.Pointer("cus_abc123"),
        Name: "Monthly API Service",
        PlanID: "plan_abc123",
        StartedAt: types.MustTimeFromString("2024-01-15T00:00:00Z"),
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

### Parameters

| Parameter                                                                                    | Type                                                                                         | Required                                                                                     | Description                                                                                  |
| -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| `ctx`                                                                                        | [context.Context](https://pkg.go.dev/context#Context)                                        | :heavy_check_mark:                                                                           | The context to use for the request.                                                          |
| `request`                                                                                    | [operations.CreateSubscriptionRequest](../../models/operations/createsubscriptionrequest.md) | :heavy_check_mark:                                                                           | The request object to use for the request.                                                   |
| `opts`                                                                                       | [][operations.Option](../../models/operations/option.md)                                     | :heavy_minus_sign:                                                                           | The options for this request.                                                                |

### Response

**[*components.Subscription](../../models/components/subscription.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## Get

Get

### Example Usage

<!-- UsageSnippet language="go" operationID="getSubscription" method="get" path="/v0/subscriptions/{id}" -->
```go
package main

import(
	"context"
	"os"
	paygentic "github.com/paygentic/sdk-go"
	"log"
	"github.com/paygentic/sdk-go/models/components"
)

func main() {
    ctx := context.Background()

    s := paygentic.New(
        paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
    )

    res, err := s.Subscriptions.Get(ctx, "<id>")
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

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | `string`                                                 | :heavy_check_mark:                                       | N/A                                                      |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*components.Subscription](../../models/components/subscription.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## GeneratePortalLink

Generates a secure, time-limited URL that allows customers to access their subscription data without authentication.

### Example Usage

<!-- UsageSnippet language="go" operationID="generatePortalLink" method="post" path="/v0/subscriptions/{id}/portal" -->
```go
package main

import(
	"context"
	"os"
	paygentic "github.com/paygentic/sdk-go"
	"log"
)

func main() {
    ctx := context.Background()

    s := paygentic.New(
        paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
    )

    res, err := s.Subscriptions.GeneratePortalLink(ctx, "<id>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                             | Type                                                                                                  | Required                                                                                              | Description                                                                                           |
| ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                 | [context.Context](https://pkg.go.dev/context#Context)                                                 | :heavy_check_mark:                                                                                    | The context to use for the request.                                                                   |
| `id`                                                                                                  | `string`                                                                                              | :heavy_check_mark:                                                                                    | The subscription ID                                                                                   |
| `body`                                                                                                | [*operations.GeneratePortalLinkRequestBody](../../models/operations/generateportallinkrequestbody.md) | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |
| `opts`                                                                                                | [][operations.Option](../../models/operations/option.md)                                              | :heavy_minus_sign:                                                                                    | The options for this request.                                                                         |

### Response

**[*components.SubscriptionPortal](../../models/components/subscriptionportal.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 401, 403, 404, 429           | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## Terminate

Terminates a subscription with a required reason. This endpoint is for merchant-initiated termination only.

### Example Usage

<!-- UsageSnippet language="go" operationID="terminateSubscription" method="post" path="/v0/subscriptions/{id}/termination" -->
```go
package main

import(
	"context"
	"os"
	paygentic "github.com/paygentic/sdk-go"
	"github.com/paygentic/sdk-go/models/operations"
	"log"
	"github.com/paygentic/sdk-go/models/components"
)

func main() {
    ctx := context.Background()

    s := paygentic.New(
        paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
    )

    res, err := s.Subscriptions.Terminate(ctx, "<id>", operations.TerminateSubscriptionRequestBody{
        Reason: "<value>",
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

### Parameters

| Parameter                                                                                                  | Type                                                                                                       | Required                                                                                                   | Description                                                                                                |
| ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                      | [context.Context](https://pkg.go.dev/context#Context)                                                      | :heavy_check_mark:                                                                                         | The context to use for the request.                                                                        |
| `id`                                                                                                       | `string`                                                                                                   | :heavy_check_mark:                                                                                         | The subscription ID                                                                                        |
| `body`                                                                                                     | [operations.TerminateSubscriptionRequestBody](../../models/operations/terminatesubscriptionrequestbody.md) | :heavy_check_mark:                                                                                         | N/A                                                                                                        |
| `opts`                                                                                                     | [][operations.Option](../../models/operations/option.md)                                                   | :heavy_minus_sign:                                                                                         | The options for this request.                                                                              |

### Response

**[*components.Subscription](../../models/components/subscription.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404, 409           | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |