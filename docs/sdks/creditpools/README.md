# CreditPools

## Overview

A `CreditPool` is the `(customer, pricingUnit)` identity that credit-denominated prices draw down. The balance itself lives on grants, not on the pool; the pool survives subscription changes. There is one pool per `(customer, pricingUnit)`.

### Available Operations

* [CreateCreditPool](#createcreditpool) - Create or resolve
* [ListCreditPools](#listcreditpools) - List
* [GetCreditPool](#getcreditpool) - Get
* [ListCreditPoolGrants](#listcreditpoolgrants) - List grants
* [CreateCreditPoolGrant](#createcreditpoolgrant) - Grant credits
* [GetCreditPoolLedger](#getcreditpoolledger) - Get ledger
* [CreateCreditPoolPurchase](#createcreditpoolpurchase) - Purchase credits

## CreateCreditPool

Resolve-or-create the credit pool for a `(customer, pricingUnit)` pair. Idempotent: returns `201` with a newly created pool, or `200` with the existing pool. Works with no subscription.

### Example Usage

<!-- UsageSnippet language="go" operationID="createCreditPool" method="post" path="/v0/creditPools" -->
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

    res, err := s.CreditPools.CreateCreditPool(ctx, operations.CreateCreditPoolRequest{
        CustomerID: "<id>",
        PricingUnitID: "<id>",
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

| Parameter                                                                                | Type                                                                                     | Required                                                                                 | Description                                                                              |
| ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| `ctx`                                                                                    | [context.Context](https://pkg.go.dev/context#Context)                                    | :heavy_check_mark:                                                                       | The context to use for the request.                                                      |
| `request`                                                                                | [operations.CreateCreditPoolRequest](../../models/operations/createcreditpoolrequest.md) | :heavy_check_mark:                                                                       | The request object to use for the request.                                               |
| `opts`                                                                                   | [][operations.Option](../../models/operations/option.md)                                 | :heavy_minus_sign:                                                                       | The options for this request.                                                            |

### Response

**[*components.CreditPool](../../models/components/creditpool.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## ListCreditPools

List

### Example Usage

<!-- UsageSnippet language="go" operationID="listCreditPools" method="get" path="/v0/creditPools" -->
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

    res, err := s.CreditPools.ListCreditPools(ctx, &operations.ListCreditPoolsRequest{})
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                              | Type                                                                                   | Required                                                                               | Description                                                                            |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| `ctx`                                                                                  | [context.Context](https://pkg.go.dev/context#Context)                                  | :heavy_check_mark:                                                                     | The context to use for the request.                                                    |
| `request`                                                                              | [operations.ListCreditPoolsRequest](../../models/operations/listcreditpoolsrequest.md) | :heavy_check_mark:                                                                     | The request object to use for the request.                                             |
| `opts`                                                                                 | [][operations.Option](../../models/operations/option.md)                               | :heavy_minus_sign:                                                                     | The options for this request.                                                          |

### Response

**[*operations.ListCreditPoolsResponse](../../models/operations/listcreditpoolsresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## GetCreditPool

Get

### Example Usage

<!-- UsageSnippet language="go" operationID="getCreditPool" method="get" path="/v0/creditPools/{id}" -->
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

    res, err := s.CreditPools.GetCreditPool(ctx, "<id>")
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
| `id`                                                     | `string`                                                 | :heavy_check_mark:                                       | N/A                                                      |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*components.CreditPool](../../models/components/creditpool.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## ListCreditPoolGrants

Lists the grants on the pool, with the credits left on each. Active and scheduled grants come first, in the order they are spent: lowest priority first, then soonest expiry (no expiry last), then oldest. Expired and voided grants come after, newest first. `remainingBalance` is the grant's balance from the same replay the ledger runs, computed at read time from the usage so far. It is 0 unless the grant is active. Statuses and balances are computed at one instant, returned as `asOf`. It defaults to the pool's current time: the test clock time of the customer's newest active subscription if it has one, otherwise now. A later `at` is read as the pool's current time. Pass `at` to read at a different instant.

### Example Usage

<!-- UsageSnippet language="go" operationID="listCreditPoolGrants" method="get" path="/v0/creditPools/{id}/grants" -->
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

    res, err := s.CreditPools.ListCreditPoolGrants(ctx, operations.ListCreditPoolGrantsRequest{
        ID: "<id>",
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

| Parameter                                                                                        | Type                                                                                             | Required                                                                                         | Description                                                                                      |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                            | [context.Context](https://pkg.go.dev/context#Context)                                            | :heavy_check_mark:                                                                               | The context to use for the request.                                                              |
| `request`                                                                                        | [operations.ListCreditPoolGrantsRequest](../../models/operations/listcreditpoolgrantsrequest.md) | :heavy_check_mark:                                                                               | The request object to use for the request.                                                       |
| `opts`                                                                                           | [][operations.Option](../../models/operations/option.md)                                         | :heavy_minus_sign:                                                                               | The options for this request.                                                                    |

### Response

**[*components.CreditPoolGrantList](../../models/components/creditpoolgrantlist.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## CreateCreditPoolGrant

Mint a credit grant on the pool. Set `recurrencePeriod` (+ optional `recurrenceAnchor`, defaults to `effectiveAt`) for a recurring grant that re-adds `amount` each interval; set `expiresAt` for a per-grant expiry. Standalone of any plan or subscription.

### Example Usage

<!-- UsageSnippet language="go" operationID="createCreditPoolGrant" method="post" path="/v0/creditPools/{id}/grants" -->
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

    res, err := s.CreditPools.CreateCreditPoolGrant(ctx, "<id>", operations.CreateCreditPoolGrantRequestBody{
        Amount: 5717.01,
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

| Parameter                                                                                                  | Type                                                                                                       | Required                                                                                                   | Description                                                                                                |
| ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                      | [context.Context](https://pkg.go.dev/context#Context)                                                      | :heavy_check_mark:                                                                                         | The context to use for the request.                                                                        |
| `id`                                                                                                       | `string`                                                                                                   | :heavy_check_mark:                                                                                         | N/A                                                                                                        |
| `body`                                                                                                     | [operations.CreateCreditPoolGrantRequestBody](../../models/operations/createcreditpoolgrantrequestbody.md) | :heavy_check_mark:                                                                                         | N/A                                                                                                        |
| `opts`                                                                                                     | [][operations.Option](../../models/operations/option.md)                                                   | :heavy_minus_sign:                                                                                         | The options for this request.                                                                              |

### Response

**[*components.CreditPoolGrant](../../models/components/creditpoolgrant.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404, 409           | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## GetCreditPoolLedger

Returns a chronologically-ordered ledger of the pool's balance history within a required time window: `increment` (a grant funded the pool, including recurrence refills), `decrement` (usage drawdown), `void` (a grant was cancelled early), and `expiration` (a grant's unused balance lapsed at expiry). Each entry carries the pool's running balance immediately before and after it, and the response reports the window's boundary balances at the top level. Pass `granularity` to receive calendar-aligned buckets instead of itemized entries. There is no full-history view in a single call — page through successive windows to see a pool's complete history.

### Example Usage

<!-- UsageSnippet language="go" operationID="getCreditPoolLedger" method="get" path="/v0/creditPools/{id}/ledger" -->
```go
package main

import(
	"context"
	"os"
	paygentic "github.com/paygentic/sdk-go"
	"github.com/paygentic/sdk-go/types"
	"github.com/paygentic/sdk-go/models/operations"
	"log"
)

func main() {
    ctx := context.Background()

    s := paygentic.New(
        paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
    )

    res, err := s.CreditPools.GetCreditPoolLedger(ctx, operations.GetCreditPoolLedgerRequest{
        ID: "<id>",
        From: types.MustTimeFromString("2025-01-03T19:47:34.571Z"),
        To: types.MustTimeFromString("2025-06-15T09:32:08.085Z"),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        switch res.Type {
            case operations.GetCreditPoolLedgerResponseTypeCreditPoolLedgerItemizedResponse:
                // res.CreditPoolLedgerItemizedResponse is populated
            case operations.GetCreditPoolLedgerResponseTypeCreditPoolLedgerBucketedResponse:
                // res.CreditPoolLedgerBucketedResponse is populated
            default:
                // Unknown type - use res.GetUnknownRaw() for raw JSON
        }

    }
}
```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `ctx`                                                                                          | [context.Context](https://pkg.go.dev/context#Context)                                          | :heavy_check_mark:                                                                             | The context to use for the request.                                                            |
| `request`                                                                                      | [operations.GetCreditPoolLedgerRequest](../../models/operations/getcreditpoolledgerrequest.md) | :heavy_check_mark:                                                                             | The request object to use for the request.                                                     |
| `opts`                                                                                         | [][operations.Option](../../models/operations/option.md)                                       | :heavy_minus_sign:                                                                             | The options for this request.                                                                  |

### Response

**[*operations.GetCreditPoolLedgerResponse](../../models/operations/getcreditpoolledgerresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## CreateCreditPoolPurchase

Create a grant-purchase invoice for the pool's customer and advance it to a payment session. Price is server-derived from the pricing unit's conversion rate — the caller never supplies a price. On successful payment, the existing billing-worker settlement path mints the purchased credits as a grant on the pool; this endpoint does not mint the grant itself.

### Example Usage

<!-- UsageSnippet language="go" operationID="createCreditPoolPurchase" method="post" path="/v0/creditPools/{id}/purchase" -->
```go
package main

import(
	"context"
	"os"
	paygentic "github.com/paygentic/sdk-go"
	"github.com/paygentic/sdk-go/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := paygentic.New(
        paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
    )

    res, err := s.CreditPools.CreateCreditPoolPurchase(ctx, "<id>", components.PoolGrantPurchaseRequest{
        GrantAmount: 5185.68,
        IdempotencyKey: "<value>",
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

| Parameter                                                                                  | Type                                                                                       | Required                                                                                   | Description                                                                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `ctx`                                                                                      | [context.Context](https://pkg.go.dev/context#Context)                                      | :heavy_check_mark:                                                                         | The context to use for the request.                                                        |
| `id`                                                                                       | `string`                                                                                   | :heavy_check_mark:                                                                         | N/A                                                                                        |
| `body`                                                                                     | [components.PoolGrantPurchaseRequest](../../models/components/poolgrantpurchaserequest.md) | :heavy_check_mark:                                                                         | N/A                                                                                        |
| `opts`                                                                                     | [][operations.Option](../../models/operations/option.md)                                   | :heavy_minus_sign:                                                                         | The options for this request.                                                              |

### Response

**[*operations.CreateCreditPoolPurchaseResponse](../../models/operations/createcreditpoolpurchaseresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404, 409           | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |