# Subscriptions

## Overview

A `Subscription` is a customer's commitment to purchase a `Product` following the terms of a `Plan` and its linked `Prices`.

### Available Operations

* [List](#list) - List
* [Create](#create) - Create
* [Get](#get) - Get
* [UpdateSubscription](#updatesubscription) - Update
* [GeneratePortalLink](#generateportallink) - Generate Portal Link
* [Terminate](#terminate) - Terminate
* [ReconcileSubscriptionFeatures](#reconcilesubscriptionfeatures) - Reconcile Features
* [ListSubscriptionAdjustments](#listsubscriptionadjustments) - List Adjustments
* [CreateSubscriptionAdjustment](#createsubscriptionadjustment) - Create Adjustment
* [DeleteSubscriptionAdjustment](#deletesubscriptionadjustment) - Delete Adjustment

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
| errors.Error                 | 401, 403, 404, 409           | application/json             |
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

## UpdateSubscription

Update

### Example Usage

<!-- UsageSnippet language="go" operationID="updateSubscription" method="patch" path="/v0/subscriptions/{id}" -->
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

    res, err := s.Subscriptions.UpdateSubscription(ctx, "<id>", operations.UpdateSubscriptionRequestBody{})
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

| Parameter                                                                                            | Type                                                                                                 | Required                                                                                             | Description                                                                                          |
| ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                | [context.Context](https://pkg.go.dev/context#Context)                                                | :heavy_check_mark:                                                                                   | The context to use for the request.                                                                  |
| `id`                                                                                                 | `string`                                                                                             | :heavy_check_mark:                                                                                   | N/A                                                                                                  |
| `body`                                                                                               | [operations.UpdateSubscriptionRequestBody](../../models/operations/updatesubscriptionrequestbody.md) | :heavy_check_mark:                                                                                   | N/A                                                                                                  |
| `opts`                                                                                               | [][operations.Option](../../models/operations/option.md)                                             | :heavy_minus_sign:                                                                                   | The options for this request.                                                                        |

### Response

**[*components.Subscription](../../models/components/subscription.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
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

## ReconcileSubscriptionFeatures

Creates a reconciliation that converges a subscription's feature entitlements to its current plan. Provisions a missing entitlement (and, for metered features, its initial grant) for every plan feature the subscription does not already have; cancels the entitlement and voids the grants of any feature no longer on the plan; then synchronizes the corresponding prices' billing. An already-present feature is left unchanged. Restricted to active subscriptions billed on their plan's line-item schedule.

### Example Usage

<!-- UsageSnippet language="go" operationID="reconcileSubscriptionFeatures" method="post" path="/v0/subscriptions/{id}/reconciliations" -->
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

    res, err := s.Subscriptions.ReconcileSubscriptionFeatures(ctx, "<id>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                   | Type                                                                                                                        | Required                                                                                                                    | Description                                                                                                                 |
| --------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                       | [context.Context](https://pkg.go.dev/context#Context)                                                                       | :heavy_check_mark:                                                                                                          | The context to use for the request.                                                                                         |
| `id`                                                                                                                        | `string`                                                                                                                    | :heavy_check_mark:                                                                                                          | The subscription ID                                                                                                         |
| `body`                                                                                                                      | [*operations.ReconcileSubscriptionFeaturesRequestBody](../../models/operations/reconcilesubscriptionfeaturesrequestbody.md) | :heavy_minus_sign:                                                                                                          | N/A                                                                                                                         |
| `opts`                                                                                                                      | [][operations.Option](../../models/operations/option.md)                                                                    | :heavy_minus_sign:                                                                                                          | The options for this request.                                                                                               |

### Response

**[*components.SubscriptionReconciliation](../../models/components/subscriptionreconciliation.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## ListSubscriptionAdjustments

Reads the adjustments on the subscription, oldest window first. A subscription with no adjustment returns an empty array. Paginated, because a long-running subscription accumulates one adjustment per rate change of every deal it has carried.

### Example Usage

<!-- UsageSnippet language="go" operationID="listSubscriptionAdjustments" method="get" path="/v0/subscriptions/{id}/adjustments" -->
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

    res, err := s.Subscriptions.ListSubscriptionAdjustments(ctx, "<id>", paygentic.Pointer("10"), paygentic.Pointer("0"))
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | `string`                                                 | :heavy_check_mark:                                       | The subscription ID                                      |
| `limit`                                                  | `*string`                                                | :heavy_minus_sign:                                       | Number of adjustments to return                          |
| `offset`                                                 | `*string`                                                | :heavy_minus_sign:                                       | Number of adjustments to skip                            |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*components.SubscriptionAdjustmentsResponse](../../models/components/subscriptionadjustmentsresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## CreateSubscriptionAdjustment

Attaches a percentage discount to the subscription for a dated window. Every invoice calculated while the window is open carries one discount line for each discounted charge, and tax is assessed on the reduced amount. An invoice that already exists is not changed, including one still in draft — the discount reaches the periods that close after it is created. There is no update operation, and a window cannot be changed after it is created. To change a rate before any invoice has issued under the discount, delete the adjustment and create a replacement. Once an invoice has issued the adjustment is permanent, so set effectiveTo at creation time whenever the deal has a known end date.

### Example Usage

<!-- UsageSnippet language="go" operationID="createSubscriptionAdjustment" method="post" path="/v0/subscriptions/{id}/adjustments" -->
```go
package main

import(
	"context"
	"os"
	paygentic "github.com/paygentic/sdk-go"
	"github.com/paygentic/sdk-go/models/components"
	"github.com/paygentic/sdk-go/types"
	"github.com/paygentic/sdk-go/optionalnullable"
	"time"
	"log"
)

func main() {
    ctx := context.Background()

    s := paygentic.New(
        paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
    )

    res, err := s.Subscriptions.CreateSubscriptionAdjustment(ctx, "<id>", components.CreateSubscriptionAdjustmentRequest{
        Type: components.CreateSubscriptionAdjustmentRequestTypePercentageDiscount,
        PercentageDiscount: "0.35",
        EffectiveFrom: types.MustTimeFromString("2026-01-01T00:00:00Z"),
        EffectiveTo: optionalnullable.From[time.Time](nil),
        Description: optionalnullable.From(paygentic.Pointer("FY26 Growth")),
        IdempotencyKey: paygentic.Pointer("adj_fy26_growth_001"),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                        | Type                                                                                                             | Required                                                                                                         | Description                                                                                                      |
| ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                            | [context.Context](https://pkg.go.dev/context#Context)                                                            | :heavy_check_mark:                                                                                               | The context to use for the request.                                                                              |
| `id`                                                                                                             | `string`                                                                                                         | :heavy_check_mark:                                                                                               | The subscription ID                                                                                              |
| `body`                                                                                                           | [components.CreateSubscriptionAdjustmentRequest](../../models/components/createsubscriptionadjustmentrequest.md) | :heavy_check_mark:                                                                                               | N/A                                                                                                              |
| `opts`                                                                                                           | [][operations.Option](../../models/operations/option.md)                                                         | :heavy_minus_sign:                                                                                               | The options for this request.                                                                                    |

### Response

**[*components.SubscriptionAdjustment](../../models/components/subscriptionadjustment.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## DeleteSubscriptionAdjustment

Deletes an adjustment that has not yet reached an issued invoice. No invoice changes: an invoice still in draft keeps its numbers, and loses the discount only when its period is calculated again. An adjustment that has already discounted an issued invoice cannot be deleted, because the invoice records why the customer was charged that amount. Its window cannot be shortened afterwards either, so set effectiveTo at creation time whenever the deal has a known end date.

### Example Usage

<!-- UsageSnippet language="go" operationID="deleteSubscriptionAdjustment" method="delete" path="/v0/subscriptions/{id}/adjustments/{adjustmentId}" -->
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

    err := s.Subscriptions.DeleteSubscriptionAdjustment(ctx, "<id>", "<id>")
    if err != nil {
        log.Fatal(err)
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | `string`                                                 | :heavy_check_mark:                                       | The subscription ID                                      |
| `adjustmentID`                                           | `string`                                                 | :heavy_check_mark:                                       | The adjustment ID                                        |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 401, 403, 404, 409           | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |