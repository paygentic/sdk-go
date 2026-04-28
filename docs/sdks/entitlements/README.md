# Entitlements

## Overview

### Available Operations

* [List](#list) - List Entitlements
* [Issue](#issue) - Issue Entitlement
* [Get](#get) - Get Entitlement

## List

Retrieve all entitlements for a customer, optionally filtered by feature or product.

### Example Usage: emptyResult

<!-- UsageSnippet language="go" operationID="listEntitlements" method="get" path="/v1/entitlements" example="emptyResult" -->
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

    res, err := s.Entitlements.List(ctx, operations.ListEntitlementsRequest{
        CustomerID: "cus_q3r4s5t6u7v8w9x0",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```
### Example Usage: expiredEntitlement

<!-- UsageSnippet language="go" operationID="listEntitlements" method="get" path="/v1/entitlements" example="expiredEntitlement" -->
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

    res, err := s.Entitlements.List(ctx, operations.ListEntitlementsRequest{
        CustomerID: "cus_q3r4s5t6u7v8w9x0",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```
### Example Usage: multipleEntitlements

<!-- UsageSnippet language="go" operationID="listEntitlements" method="get" path="/v1/entitlements" example="multipleEntitlements" -->
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

    res, err := s.Entitlements.List(ctx, operations.ListEntitlementsRequest{
        CustomerID: "cus_q3r4s5t6u7v8w9x0",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```
### Example Usage: staticFeatureWithConfig

<!-- UsageSnippet language="go" operationID="listEntitlements" method="get" path="/v1/entitlements" example="staticFeatureWithConfig" -->
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

    res, err := s.Entitlements.List(ctx, operations.ListEntitlementsRequest{
        CustomerID: "cus_q3r4s5t6u7v8w9x0",
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
| `request`                                                                                | [operations.ListEntitlementsRequest](../../models/operations/listentitlementsrequest.md) | :heavy_check_mark:                                                                       | The request object to use for the request.                                               |
| `opts`                                                                                   | [][operations.Option](../../models/operations/option.md)                                 | :heavy_minus_sign:                                                                       | The options for this request.                                                            |

### Response

**[*operations.ListEntitlementsResponse](../../models/operations/listentitlementsresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 403                          | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## Issue

Issue a new entitlement to a customer, granting them access to a specific feature. The feature must exist and belong to the same merchant as the customer.

### Example Usage: booleanEntitlement

<!-- UsageSnippet language="go" operationID="issueEntitlement" method="post" path="/v1/entitlements" example="booleanEntitlement" -->
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

    res, err := s.Entitlements.Issue(ctx, components.IssueEntitlementRequest{
        CustomerID: "cus_q3r4s5t6u7v8w9x0",
        FeatureID: "feat_a1b2c3d4e5f6g7h8",
        Template: components.CreateEntitlementTemplateBoolean(
            components.EntitlementTemplateBoolean{},
        ),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```
### Example Usage: staticEntitlement

<!-- UsageSnippet language="go" operationID="issueEntitlement" method="post" path="/v1/entitlements" example="staticEntitlement" -->
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

    res, err := s.Entitlements.Issue(ctx, components.IssueEntitlementRequest{
        CustomerID: "cus_q3r4s5t6u7v8w9x0",
        FeatureID: "feat_a1b2c3d4e5f6g7h8",
        Template: components.CreateEntitlementTemplateStatic(
            components.EntitlementTemplateStatic{
                Config: map[string]any{
                    "limit": 25,
                    "tier": "pro",
                },
            },
        ),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```
### Example Usage: timedEntitlement

<!-- UsageSnippet language="go" operationID="issueEntitlement" method="post" path="/v1/entitlements" example="timedEntitlement" -->
```go
package main

import(
	"context"
	"os"
	paygentic "github.com/paygentic/sdk-go"
	"github.com/paygentic/sdk-go/models/components"
	"github.com/paygentic/sdk-go/types"
	"github.com/paygentic/sdk-go/optionalnullable"
	"log"
)

func main() {
    ctx := context.Background()

    s := paygentic.New(
        paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
    )

    res, err := s.Entitlements.Issue(ctx, components.IssueEntitlementRequest{
        CustomerID: "cus_q3r4s5t6u7v8w9x0",
        FeatureID: "feat_a1b2c3d4e5f6g7h8",
        Template: components.CreateEntitlementTemplateBoolean(
            components.EntitlementTemplateBoolean{},
        ),
        ActiveFrom: types.MustNewTimeFromString("2024-01-01T00:00:00Z"),
        ActiveTo: optionalnullable.From(paygentic.Pointer(types.MustNewTimeFromString("2025-01-01T00:00:00Z"))),
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
| `request`                                                                                | [components.IssueEntitlementRequest](../../models/components/issueentitlementrequest.md) | :heavy_check_mark:                                                                       | The request object to use for the request.                                               |
| `opts`                                                                                   | [][operations.Option](../../models/operations/option.md)                                 | :heavy_minus_sign:                                                                       | The options for this request.                                                            |

### Response

**[*components.Entitlement](../../models/components/entitlement.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 403, 404, 409                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## Get

Retrieve a specific entitlement by ID. For metered entitlements, the response includes live balance, usage, and access status for the current billing period.

### Example Usage: booleanEntitlement

<!-- UsageSnippet language="go" operationID="getEntitlement" method="get" path="/v1/entitlements/{entitlementId}" example="booleanEntitlement" -->
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

    res, err := s.Entitlements.Get(ctx, "<id>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        switch res.Type {
            case components.EntitlementDetailTypeBoolean:
                // res.BooleanEntitlementDetail is populated
            case components.EntitlementDetailTypeStatic:
                // res.StaticEntitlementDetail is populated
            case components.EntitlementDetailTypeMetered:
                // res.MeteredEntitlementDetail is populated
            default:
                // Unknown type - use res.GetUnknownRaw() for raw JSON
        }

    }
}
```
### Example Usage: meteredEntitlement

<!-- UsageSnippet language="go" operationID="getEntitlement" method="get" path="/v1/entitlements/{entitlementId}" example="meteredEntitlement" -->
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

    res, err := s.Entitlements.Get(ctx, "<id>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        switch res.Type {
            case components.EntitlementDetailTypeBoolean:
                // res.BooleanEntitlementDetail is populated
            case components.EntitlementDetailTypeStatic:
                // res.StaticEntitlementDetail is populated
            case components.EntitlementDetailTypeMetered:
                // res.MeteredEntitlementDetail is populated
            default:
                // Unknown type - use res.GetUnknownRaw() for raw JSON
        }

    }
}
```
### Example Usage: staticEntitlement

<!-- UsageSnippet language="go" operationID="getEntitlement" method="get" path="/v1/entitlements/{entitlementId}" example="staticEntitlement" -->
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

    res, err := s.Entitlements.Get(ctx, "<id>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        switch res.Type {
            case components.EntitlementDetailTypeBoolean:
                // res.BooleanEntitlementDetail is populated
            case components.EntitlementDetailTypeStatic:
                // res.StaticEntitlementDetail is populated
            case components.EntitlementDetailTypeMetered:
                // res.MeteredEntitlementDetail is populated
            default:
                // Unknown type - use res.GetUnknownRaw() for raw JSON
        }

    }
}
```

### Parameters

| Parameter                                                                                                                                                                    | Type                                                                                                                                                                         | Required                                                                                                                                                                     | Description                                                                                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                                                                        | [context.Context](https://pkg.go.dev/context#Context)                                                                                                                        | :heavy_check_mark:                                                                                                                                                           | The context to use for the request.                                                                                                                                          |
| `entitlementID`                                                                                                                                                              | `string`                                                                                                                                                                     | :heavy_check_mark:                                                                                                                                                           | The unique identifier of the entitlement.                                                                                                                                    |
| `at`                                                                                                                                                                         | [*time.Time](https://pkg.go.dev/time#Time)                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                           | Evaluate balance and access at this point in time (RFC 3339 datetime with any UTC offset, e.g. 2024-01-15T10:30:00Z or 2024-01-15T15:30:00+05:30). Defaults to current time. |
| `opts`                                                                                                                                                                       | [][operations.Option](../../models/operations/option.md)                                                                                                                     | :heavy_minus_sign:                                                                                                                                                           | The options for this request.                                                                                                                                                |

### Response

**[*components.EntitlementDetail](../../models/components/entitlementdetail.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 403, 404                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |