# MerchantIntegrations

## Overview

A `MerchantIntegration` records a merchant's connection to an external provider. One connection per `(merchant, provider)` — re-connecting upserts in place.

### Available Operations

* [ListMerchantIntegrations](#listmerchantintegrations) - List
* [UpsertMerchantIntegration](#upsertmerchantintegration) - Upsert
* [GetMerchantIntegration](#getmerchantintegration) - Get
* [DisconnectMerchantIntegration](#disconnectmerchantintegration) - Disconnect

## ListMerchantIntegrations

List

### Example Usage

<!-- UsageSnippet language="go" operationID="listMerchantIntegrations" method="get" path="/v0/merchantIntegrations" -->
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

    res, err := s.MerchantIntegrations.ListMerchantIntegrations(ctx, nil, nil, paygentic.Pointer[int64](50), paygentic.Pointer[int64](0))
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                         | Type                                                                                              | Required                                                                                          | Description                                                                                       |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                             | [context.Context](https://pkg.go.dev/context#Context)                                             | :heavy_check_mark:                                                                                | The context to use for the request.                                                               |
| `merchantID`                                                                                      | `*string`                                                                                         | :heavy_minus_sign:                                                                                | Restrict results to a specific merchant. All active filters AND together.                         |
| `provider`                                                                                        | [*components.MerchantIntegrationProvider](../../models/components/merchantintegrationprovider.md) | :heavy_minus_sign:                                                                                | Filter by provider (e.g. `salesforce`).                                                           |
| `limit`                                                                                           | `*int64`                                                                                          | :heavy_minus_sign:                                                                                | N/A                                                                                               |
| `offset`                                                                                          | `*int64`                                                                                          | :heavy_minus_sign:                                                                                | N/A                                                                                               |
| `opts`                                                                                            | [][operations.Option](../../models/operations/option.md)                                          | :heavy_minus_sign:                                                                                | The options for this request.                                                                     |

### Response

**[*operations.ListMerchantIntegrationsResponse](../../models/operations/listmerchantintegrationsresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## UpsertMerchantIntegration

Create or re-activate a merchant's connection to a provider. Idempotent on `(merchantId, provider)` — connecting an already-connected provider re-activates the existing row, never creating a duplicate.

### Example Usage

<!-- UsageSnippet language="go" operationID="upsertMerchantIntegration" method="put" path="/v0/merchantIntegrations" -->
```go
package main

import(
	"context"
	"os"
	paygentic "github.com/paygentic/sdk-go"
	"github.com/paygentic/sdk-go/models/components"
	"github.com/paygentic/sdk-go/models/operations"
	"log"
)

func main() {
    ctx := context.Background()

    s := paygentic.New(
        paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
    )

    res, err := s.MerchantIntegrations.UpsertMerchantIntegration(ctx, operations.UpsertMerchantIntegrationRequest{
        MerchantID: "<id>",
        Provider: components.MerchantIntegrationProviderSalesforce,
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
| `request`                                                                                                  | [operations.UpsertMerchantIntegrationRequest](../../models/operations/upsertmerchantintegrationrequest.md) | :heavy_check_mark:                                                                                         | The request object to use for the request.                                                                 |
| `opts`                                                                                                     | [][operations.Option](../../models/operations/option.md)                                                   | :heavy_minus_sign:                                                                                         | The options for this request.                                                                              |

### Response

**[*components.MerchantIntegration](../../models/components/merchantintegration.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## GetMerchantIntegration

Get

### Example Usage

<!-- UsageSnippet language="go" operationID="getMerchantIntegration" method="get" path="/v0/merchantIntegrations/{id}" -->
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

    res, err := s.MerchantIntegrations.GetMerchantIntegration(ctx, "<id>")
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
| `id`                                                     | `string`                                                 | :heavy_check_mark:                                       | The unique identifier of the merchant integration        |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*components.MerchantIntegration](../../models/components/merchantintegration.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## DisconnectMerchantIntegration

Soft-disconnect a connection (status `disconnected`, stamp `disconnectedAt`). Never hard-deletes — preserves the install id and `connectedAt` for audit.

### Example Usage

<!-- UsageSnippet language="go" operationID="disconnectMerchantIntegration" method="patch" path="/v0/merchantIntegrations/{id}/disconnect" -->
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

    res, err := s.MerchantIntegrations.DisconnectMerchantIntegration(ctx, "<id>")
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
| `id`                                                     | `string`                                                 | :heavy_check_mark:                                       | The unique identifier of the merchant integration        |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*components.MerchantIntegration](../../models/components/merchantintegration.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |