# Prices

## Overview

A `Price` determines the monetary value for a single unit of a `Billable Metric`. Prices are exclusively grouped within a `Plan`.

### Available Operations

* [Create](#create) - Create
* [List](#list) - List
* [Get](#get) - Get
* [Update](#update) - Update
* [Delete](#delete) - Delete

## Create

Create

### Example Usage

<!-- UsageSnippet language="go" operationID="createPrice" method="post" path="/v0/prices" -->
```go
package main

import(
	"context"
	"os"
	paygentic "github.com/paygentic/sdk-go"
	"github.com/paygentic/sdk-go/models/operations"
	"github.com/paygentic/sdk-go/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := paygentic.New(
        paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
    )

    res, err := s.Prices.Create(ctx, operations.CreatePriceRequest{
        InvoiceDisplayName: "<value>",
        PaymentTerm: operations.CreatePricePaymentTermInstant,
        Properties: components.CreatePricePropertiesUnionPriceProperties3(
            components.PriceProperties3{
                Default: "<value>",
                Parameters: components.Parameters{
                    Function: components.FunctionLinear,
                    Gradient: "<value>",
                    Max: "<value>",
                    Min: "<value>",
                },
            },
        ),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        switch res.Properties.Type {
            case components.PricePropertiesUnionTypePriceProperties1:
                // res.Properties.PriceProperties1 is populated
            case components.PricePropertiesUnionTypePriceProperties2:
                // res.Properties.PriceProperties2 is populated
            case components.PricePropertiesUnionTypePriceProperties3:
                // res.Properties.PriceProperties3 is populated
            case components.PricePropertiesUnionTypePriceProperties4:
                // res.Properties.PriceProperties4 is populated
            default:
                // Unknown type - use res.Properties.GetUnknownRaw() for raw JSON
        }

    }
}
```

### Parameters

| Parameter                                                                      | Type                                                                           | Required                                                                       | Description                                                                    |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `ctx`                                                                          | [context.Context](https://pkg.go.dev/context#Context)                          | :heavy_check_mark:                                                             | The context to use for the request.                                            |
| `request`                                                                      | [operations.CreatePriceRequest](../../models/operations/createpricerequest.md) | :heavy_check_mark:                                                             | The request object to use for the request.                                     |
| `opts`                                                                         | [][operations.Option](../../models/operations/option.md)                       | :heavy_minus_sign:                                                             | The options for this request.                                                  |

### Response

**[*components.SchemasPrice](../../models/components/schemasprice.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## List

List

### Example Usage

<!-- UsageSnippet language="go" operationID="listPrices" method="get" path="/v0/prices" -->
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

    res, err := s.Prices.List(ctx, nil, paygentic.Pointer[int64](10), paygentic.Pointer[int64](0))
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
| `billableMetricID`                                       | `*string`                                                | :heavy_minus_sign:                                       | Filter prices by billable metric ID                      |
| `limit`                                                  | `*int64`                                                 | :heavy_minus_sign:                                       | Number of prices to return                               |
| `offset`                                                 | `*int64`                                                 | :heavy_minus_sign:                                       | Number of prices to skip                                 |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.ListPricesResponse](../../models/operations/listpricesresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## Get

Get

### Example Usage

<!-- UsageSnippet language="go" operationID="getPrice" method="get" path="/v0/prices/{id}" -->
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

    res, err := s.Prices.Get(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        switch res.Properties.Type {
            case components.PricePropertiesUnionTypePriceProperties1:
                // res.Properties.PriceProperties1 is populated
            case components.PricePropertiesUnionTypePriceProperties2:
                // res.Properties.PriceProperties2 is populated
            case components.PricePropertiesUnionTypePriceProperties3:
                // res.Properties.PriceProperties3 is populated
            case components.PricePropertiesUnionTypePriceProperties4:
                // res.Properties.PriceProperties4 is populated
            default:
                // Unknown type - use res.Properties.GetUnknownRaw() for raw JSON
        }

    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | `string`                                                 | :heavy_check_mark:                                       | The unique identifier of the price                       |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*components.SchemasPrice](../../models/components/schemasprice.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## Update

Update

### Example Usage

<!-- UsageSnippet language="go" operationID="updatePrice" method="patch" path="/v0/prices/{id}" -->
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

    res, err := s.Prices.Update(ctx, "<id>", operations.UpdatePriceRequestBody{})
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        switch res.Properties.Type {
            case components.PricePropertiesUnionTypePriceProperties1:
                // res.Properties.PriceProperties1 is populated
            case components.PricePropertiesUnionTypePriceProperties2:
                // res.Properties.PriceProperties2 is populated
            case components.PricePropertiesUnionTypePriceProperties3:
                // res.Properties.PriceProperties3 is populated
            case components.PricePropertiesUnionTypePriceProperties4:
                // res.Properties.PriceProperties4 is populated
            default:
                // Unknown type - use res.Properties.GetUnknownRaw() for raw JSON
        }

    }
}
```

### Parameters

| Parameter                                                                              | Type                                                                                   | Required                                                                               | Description                                                                            |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| `ctx`                                                                                  | [context.Context](https://pkg.go.dev/context#Context)                                  | :heavy_check_mark:                                                                     | The context to use for the request.                                                    |
| `id`                                                                                   | `string`                                                                               | :heavy_check_mark:                                                                     | The unique identifier of the price                                                     |
| `body`                                                                                 | [operations.UpdatePriceRequestBody](../../models/operations/updatepricerequestbody.md) | :heavy_check_mark:                                                                     | N/A                                                                                    |
| `opts`                                                                                 | [][operations.Option](../../models/operations/option.md)                               | :heavy_minus_sign:                                                                     | The options for this request.                                                          |

### Response

**[*components.SchemasPrice](../../models/components/schemasprice.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## Delete

Delete

### Example Usage

<!-- UsageSnippet language="go" operationID="deletePrice" method="delete" path="/v0/prices/{id}" -->
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

    err := s.Prices.Delete(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | `string`                                                 | :heavy_check_mark:                                       | The unique identifier of the price                       |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |