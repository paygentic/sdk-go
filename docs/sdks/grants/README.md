# Entitlements.Grants

## Overview

### Available Operations

* [List](#list) - List Grants
* [Create](#create) - Create Grant
* [Purchase](#purchase) - Purchase Grant
* [Get](#get) - Get Grant
* [Void](#void) - Void Grant

## List

List grants for a metered entitlement. Active grants are returned by default; pass `includeVoided=true` to include voided grants.

### Example Usage

<!-- UsageSnippet language="go" operationID="listEntitlementGrants" method="get" path="/v1/entitlements/{entitlementId}/grants" -->
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

    res, err := s.Entitlements.Grants.List(ctx, "<id>", paygentic.Pointer[int64](20), paygentic.Pointer[int64](0), paygentic.Pointer(false))
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
| `entitlementID`                                          | `string`                                                 | :heavy_check_mark:                                       | The unique identifier of the entitlement.                |
| `limit`                                                  | `*int64`                                                 | :heavy_minus_sign:                                       | Maximum number of grants to return per page.             |
| `offset`                                                 | `*int64`                                                 | :heavy_minus_sign:                                       | Number of grants to skip.                                |
| `includeVoided`                                          | `*bool`                                                  | :heavy_minus_sign:                                       | When true, voided grants are included in the response.   |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.ListEntitlementGrantsResponse](../../models/operations/listentitlementgrantsresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 403, 404                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## Create

Create a grant directly for a metered entitlement, crediting the customer's balance immediately. The entitlement must belong to an active v1 subscription.

### Example Usage: minimal

<!-- UsageSnippet language="go" operationID="createEntitlementGrant" method="post" path="/v1/entitlements/{entitlementId}/grants" example="minimal" -->
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

    res, err := s.Entitlements.Grants.Create(ctx, "<id>", components.CreateGrantRequest{
        Amount: 100.0,
        IdempotencyKey: "grant-initial-100",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```
### Example Usage: withExpiry

<!-- UsageSnippet language="go" operationID="createEntitlementGrant" method="post" path="/v1/entitlements/{entitlementId}/grants" example="withExpiry" -->
```go
package main

import(
	"context"
	"os"
	paygentic "github.com/paygentic/sdk-go"
	"github.com/paygentic/sdk-go/types"
	"github.com/paygentic/sdk-go/optionalnullable"
	"github.com/paygentic/sdk-go/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := paygentic.New(
        paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
    )

    res, err := s.Entitlements.Grants.Create(ctx, "<id>", components.CreateGrantRequest{
        Amount: 500.0,
        EffectiveAt: types.MustNewTimeFromString("2026-03-14T00:00:00Z"),
        ExpiresAt: optionalnullable.From(paygentic.Pointer(types.MustNewTimeFromString("2026-04-14T00:00:00Z"))),
        IdempotencyKey: "grant-march-2026-promo",
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

| Parameter                                                                      | Type                                                                           | Required                                                                       | Description                                                                    |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `ctx`                                                                          | [context.Context](https://pkg.go.dev/context#Context)                          | :heavy_check_mark:                                                             | The context to use for the request.                                            |
| `entitlementID`                                                                | `string`                                                                       | :heavy_check_mark:                                                             | The unique identifier of the entitlement to grant credits to.                  |
| `body`                                                                         | [components.CreateGrantRequest](../../models/components/creategrantrequest.md) | :heavy_check_mark:                                                             | N/A                                                                            |
| `opts`                                                                         | [][operations.Option](../../models/operations/option.md)                       | :heavy_minus_sign:                                                             | The options for this request.                                                  |

### Response

**[*components.Grant](../../models/components/grant.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 403, 404, 409                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## Purchase

Create an ad-hoc invoice with a payment session for a grant purchase. The customer pays via the returned payment URL; the grant is created automatically on payment completion. If payment expires, the invoice is cancelled and no grant is created.

After the consumer completes payment, the grant is created automatically. To confirm payment completion, poll `GET /v2/invoices/{invoiceId}` using the `invoiceId` from the response and check for `status === "PAID"`. Recommended polling interval: 2 seconds, timeout: 60 seconds.

### Example Usage: basic

<!-- UsageSnippet language="go" operationID="purchaseEntitlementGrant" method="post" path="/v1/entitlements/{entitlementId}/grants/purchase" example="basic" -->
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

    res, err := s.Entitlements.Grants.Purchase(ctx, "<id>", components.PurchaseGrantRequest{
        Amount: 1000.0,
        Price: "5.00",
        IdempotencyKey: "purchase-march-2026-topup",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```
### Example Usage: withOptions

<!-- UsageSnippet language="go" operationID="purchaseEntitlementGrant" method="post" path="/v1/entitlements/{entitlementId}/grants/purchase" example="withOptions" -->
```go
package main

import(
	"context"
	"os"
	paygentic "github.com/paygentic/sdk-go"
	"github.com/paygentic/sdk-go/types"
	"github.com/paygentic/sdk-go/optionalnullable"
	"github.com/paygentic/sdk-go/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := paygentic.New(
        paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
    )

    res, err := s.Entitlements.Grants.Purchase(ctx, "<id>", components.PurchaseGrantRequest{
        Amount: 500.0,
        Price: "2.50",
        IdempotencyKey: "purchase-promo-500",
        EffectiveAt: types.MustNewTimeFromString("2026-03-14T00:00:00Z"),
        ExpiresAt: optionalnullable.From(paygentic.Pointer(types.MustNewTimeFromString("2026-04-14T00:00:00Z"))),
        SuccessURL: paygentic.Pointer("https://example.com/success"),
        CancelURL: paygentic.Pointer("https://example.com/cancel"),
        PaymentExpiresAt: types.MustNewTimeFromString("2026-03-15T00:00:00Z"),
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

| Parameter                                                                          | Type                                                                               | Required                                                                           | Description                                                                        |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `ctx`                                                                              | [context.Context](https://pkg.go.dev/context#Context)                              | :heavy_check_mark:                                                                 | The context to use for the request.                                                |
| `entitlementID`                                                                    | `string`                                                                           | :heavy_check_mark:                                                                 | The unique identifier of the entitlement to purchase credits for.                  |
| `body`                                                                             | [components.PurchaseGrantRequest](../../models/components/purchasegrantrequest.md) | :heavy_check_mark:                                                                 | N/A                                                                                |
| `opts`                                                                             | [][operations.Option](../../models/operations/option.md)                           | :heavy_minus_sign:                                                                 | The options for this request.                                                      |

### Response

**[*components.PurchaseGrantResponse](../../models/components/purchasegrantresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 403, 404, 409                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## Get

Retrieve a specific grant by ID.

### Example Usage

<!-- UsageSnippet language="go" operationID="getEntitlementGrant" method="get" path="/v1/entitlements/{entitlementId}/grants/{grantId}" -->
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

    res, err := s.Entitlements.Grants.Get(ctx, "<id>", "<id>")
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
| `entitlementID`                                          | `string`                                                 | :heavy_check_mark:                                       | The unique identifier of the entitlement.                |
| `grantID`                                                | `string`                                                 | :heavy_check_mark:                                       | The unique identifier of the grant.                      |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*components.Grant](../../models/components/grant.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 403, 404                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## Void

Void a grant, removing it from the customer's balance. This operation is idempotent — voiding an already-voided grant returns the voided grant without error.

### Example Usage

<!-- UsageSnippet language="go" operationID="voidEntitlementGrant" method="delete" path="/v1/entitlements/{entitlementId}/grants/{grantId}" -->
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

    res, err := s.Entitlements.Grants.Void(ctx, "<id>", "<id>")
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
| `entitlementID`                                          | `string`                                                 | :heavy_check_mark:                                       | The unique identifier of the entitlement.                |
| `grantID`                                                | `string`                                                 | :heavy_check_mark:                                       | The unique identifier of the grant to void.              |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*components.Grant](../../models/components/grant.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 403, 404                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |