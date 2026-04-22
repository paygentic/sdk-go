# UsageEvents

## Overview

### Available Operations

* [Create](#create) - Create
* [List](#list) - List
* [Get](#get) - Get
* [Refund](#refund) - Refund
* [BatchCreate](#batchcreate) - Batch Create

## Create

Creates a usage event. The idempotencyKey is used to ensure the event is processed only once by downstream consumers, even if the same event is submitted multiple times. Duplicate submissions will be accepted and return the same response.

### Example Usage

<!-- UsageSnippet language="go" operationID="createUsageEvent" method="post" path="/v0/usage" -->
```go
package main

import(
	"context"
	"os"
	paygentic "github.com/paygentic/sdk-go"
	"github.com/paygentic/sdk-go/models/components"
	"github.com/paygentic/sdk-go/types"
	"log"
)

func main() {
    ctx := context.Background()

    s := paygentic.New(
        paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
    )

    res, err := s.UsageEvents.Create(ctx, components.CreateUsageEventRequest{
        CustomerID: "<id>",
        IdempotencyKey: "<value>",
        MerchantID: "<id>",
        Properties: []components.CreateUsageEventRequestProperty{},
        Timestamp: types.MustTimeFromString("2026-05-14T00:54:35.100Z"),
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
| `request`                                                                                | [components.CreateUsageEventRequest](../../models/components/createusageeventrequest.md) | :heavy_check_mark:                                                                       | The request object to use for the request.                                               |
| `opts`                                                                                   | [][operations.Option](../../models/operations/option.md)                                 | :heavy_minus_sign:                                                                       | The options for this request.                                                            |

### Response

**[*components.UsageEvent](../../models/components/usageevent.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 403                          | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## List

List

### Example Usage

<!-- UsageSnippet language="go" operationID="listUsageEvents" method="get" path="/v0/usage" -->
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

    res, err := s.UsageEvents.List(ctx, operations.ListUsageEventsRequest{
        EndTime: types.MustTimeFromString("2026-03-29T00:23:32.822Z"),
        StartTime: types.MustTimeFromString("2024-02-04T03:47:15.138Z"),
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

| Parameter                                                                              | Type                                                                                   | Required                                                                               | Description                                                                            |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| `ctx`                                                                                  | [context.Context](https://pkg.go.dev/context#Context)                                  | :heavy_check_mark:                                                                     | The context to use for the request.                                                    |
| `request`                                                                              | [operations.ListUsageEventsRequest](../../models/operations/listusageeventsrequest.md) | :heavy_check_mark:                                                                     | The request object to use for the request.                                             |
| `opts`                                                                                 | [][operations.Option](../../models/operations/option.md)                               | :heavy_minus_sign:                                                                     | The options for this request.                                                          |

### Response

**[*operations.ListUsageEventsResponse](../../models/operations/listusageeventsresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 403                          | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## Get

Get

### Example Usage

<!-- UsageSnippet language="go" operationID="getUsageEvent" method="get" path="/v0/usage/{id}" -->
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

    res, err := s.UsageEvents.Get(ctx, "<id>")
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

**[*components.UsageEvent](../../models/components/usageevent.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 403, 404                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## Refund

Marks a usage event as refunded. This reverts the consumption recorded by the usage event and creates a corresponding refund billing event if the usage event was already billed.

### Example Usage

<!-- UsageSnippet language="go" operationID="refundUsageEvent" method="patch" path="/v0/usage/{id}" -->
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

    res, err := s.UsageEvents.Refund(ctx, "<id>", operations.RefundUsageEventRequestBody{})
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
| `id`                                                                                             | `string`                                                                                         | :heavy_check_mark:                                                                               | N/A                                                                                              |
| `body`                                                                                           | [operations.RefundUsageEventRequestBody](../../models/operations/refundusageeventrequestbody.md) | :heavy_check_mark:                                                                               | N/A                                                                                              |
| `opts`                                                                                           | [][operations.Option](../../models/operations/option.md)                                         | :heavy_minus_sign:                                                                               | The options for this request.                                                                    |

### Response

**[*components.UsageEvent](../../models/components/usageevent.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 403, 404, 422                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## BatchCreate

Creates multiple usage events in a single request. The idempotencyKey for each event is used to ensure the event is processed only once by downstream consumers, even if the same event is submitted multiple times. Duplicate submissions will be accepted and return the same response.

### Example Usage

<!-- UsageSnippet language="go" operationID="batchCreateUsageEvents" method="post" path="/v0/usage/batch" -->
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

    res, err := s.UsageEvents.BatchCreate(ctx, operations.BatchCreateUsageEventsRequest{
        Events: []components.CreateUsageEventRequest{},
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

| Parameter                                                                                            | Type                                                                                                 | Required                                                                                             | Description                                                                                          |
| ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                | [context.Context](https://pkg.go.dev/context#Context)                                                | :heavy_check_mark:                                                                                   | The context to use for the request.                                                                  |
| `request`                                                                                            | [operations.BatchCreateUsageEventsRequest](../../models/operations/batchcreateusageeventsrequest.md) | :heavy_check_mark:                                                                                   | The request object to use for the request.                                                           |
| `opts`                                                                                               | [][operations.Option](../../models/operations/option.md)                                             | :heavy_minus_sign:                                                                                   | The options for this request.                                                                        |

### Response

**[*components.BatchUsageEventResponse](../../models/components/batchusageeventresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 403                          | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |