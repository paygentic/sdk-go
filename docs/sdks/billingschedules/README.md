# BillingSchedules

## Overview

Owner-polymorphic billing schedules with intervals and staged invoice projections. A BillingSchedule belongs to exactly one Order or one Subscription (XOR). Cadence lives on ScheduleIntervals (cadence-on-the-line).

### Available Operations

* [ListBillingSchedules](#listbillingschedules) - List billing schedules
* [CreateBillingSchedule](#createbillingschedule) - Create a billing schedule
* [GetBillingSchedule](#getbillingschedule) - Get a billing schedule
* [UpdateBillingSchedule](#updatebillingschedule) - Update a billing schedule
* [DeleteBillingSchedule](#deletebillingschedule) - Delete a billing schedule
* [ListScheduleIntervals](#listscheduleintervals) - List schedule intervals
* [ReplaceScheduleIntervals](#replacescheduleintervals) - Replace schedule intervals
* [ListScheduleInvoices](#listscheduleinvoices) - List staged invoices
* [GenerateScheduleInvoices](#generatescheduleinvoices) - Generate staged invoices

## ListBillingSchedules

List billing schedules

### Example Usage

<!-- UsageSnippet language="go" operationID="listBillingSchedules" method="get" path="/v0/billingSchedules" -->
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

    res, err := s.BillingSchedules.ListBillingSchedules(ctx, nil, nil)
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
| `orderID`                                                | `*string`                                                | :heavy_minus_sign:                                       | Filter by owning order (XOR with subscriptionId)         |
| `subscriptionID`                                         | `*string`                                                | :heavy_minus_sign:                                       | Filter by owning subscription (XOR with orderId)         |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.ListBillingSchedulesResponse](../../models/operations/listbillingschedulesresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## CreateBillingSchedule

Create a billing schedule

### Example Usage

<!-- UsageSnippet language="go" operationID="createBillingSchedule" method="post" path="/v0/billingSchedules" -->
```go
package main

import(
	"context"
	"os"
	paygentic "github.com/paygentic/sdk-go"
	"github.com/paygentic/sdk-go/types"
	"github.com/paygentic/sdk-go/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := paygentic.New(
        paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
    )

    res, err := s.BillingSchedules.CreateBillingSchedule(ctx, components.CreateBillingScheduleRequest{
        StartDate: types.MustTimeFromString("2025-12-16T18:30:43.578Z"),
        EndDate: types.MustTimeFromString("2024-09-07T07:24:23.517Z"),
        BillingAnchor: types.MustTimeFromString("2025-10-01T16:17:23.367Z"),
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

| Parameter                                                                                          | Type                                                                                               | Required                                                                                           | Description                                                                                        |
| -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                              | [context.Context](https://pkg.go.dev/context#Context)                                              | :heavy_check_mark:                                                                                 | The context to use for the request.                                                                |
| `request`                                                                                          | [components.CreateBillingScheduleRequest](../../models/components/createbillingschedulerequest.md) | :heavy_check_mark:                                                                                 | The request object to use for the request.                                                         |
| `opts`                                                                                             | [][operations.Option](../../models/operations/option.md)                                           | :heavy_minus_sign:                                                                                 | The options for this request.                                                                      |

### Response

**[*components.SchemasBillingSchedule](../../models/components/schemasbillingschedule.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404, 409           | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## GetBillingSchedule

Get a billing schedule

### Example Usage

<!-- UsageSnippet language="go" operationID="getBillingSchedule" method="get" path="/v0/billingSchedules/{id}" -->
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

    res, err := s.BillingSchedules.GetBillingSchedule(ctx, "<id>")
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

**[*components.SchemasBillingSchedule](../../models/components/schemasbillingschedule.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## UpdateBillingSchedule

Update a billing schedule

### Example Usage

<!-- UsageSnippet language="go" operationID="updateBillingSchedule" method="patch" path="/v0/billingSchedules/{id}" -->
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

    res, err := s.BillingSchedules.UpdateBillingSchedule(ctx, "<id>", components.UpdateBillingScheduleRequest{})
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                          | Type                                                                                               | Required                                                                                           | Description                                                                                        |
| -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                              | [context.Context](https://pkg.go.dev/context#Context)                                              | :heavy_check_mark:                                                                                 | The context to use for the request.                                                                |
| `id`                                                                                               | `string`                                                                                           | :heavy_check_mark:                                                                                 | N/A                                                                                                |
| `body`                                                                                             | [components.UpdateBillingScheduleRequest](../../models/components/updatebillingschedulerequest.md) | :heavy_check_mark:                                                                                 | N/A                                                                                                |
| `opts`                                                                                             | [][operations.Option](../../models/operations/option.md)                                           | :heavy_minus_sign:                                                                                 | The options for this request.                                                                      |

### Response

**[*components.SchemasBillingSchedule](../../models/components/schemasbillingschedule.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404, 409           | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## DeleteBillingSchedule

Delete a billing schedule

### Example Usage

<!-- UsageSnippet language="go" operationID="deleteBillingSchedule" method="delete" path="/v0/billingSchedules/{id}" -->
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

    err := s.BillingSchedules.DeleteBillingSchedule(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
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

**error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## ListScheduleIntervals

List schedule intervals

### Example Usage

<!-- UsageSnippet language="go" operationID="listScheduleIntervals" method="get" path="/v0/billingSchedules/{id}/intervals" -->
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

    res, err := s.BillingSchedules.ListScheduleIntervals(ctx, "<id>")
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

**[*operations.ListScheduleIntervalsResponse](../../models/operations/listscheduleintervalsresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## ReplaceScheduleIntervals

Replace (PUT semantics) the full interval set for a schedule. Wipes existing intervals and recreates from the supplied list. Reverts any in-flight order approval for order-owned schedules.

### Example Usage

<!-- UsageSnippet language="go" operationID="replaceScheduleIntervals" method="put" path="/v0/billingSchedules/{id}/intervals" -->
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

    res, err := s.BillingSchedules.ReplaceScheduleIntervals(ctx, "<id>", components.ReplaceScheduleIntervalsRequest{
        Intervals: []components.Interval{},
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

| Parameter                                                                                                | Type                                                                                                     | Required                                                                                                 | Description                                                                                              |
| -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                    | [context.Context](https://pkg.go.dev/context#Context)                                                    | :heavy_check_mark:                                                                                       | The context to use for the request.                                                                      |
| `id`                                                                                                     | `string`                                                                                                 | :heavy_check_mark:                                                                                       | N/A                                                                                                      |
| `body`                                                                                                   | [components.ReplaceScheduleIntervalsRequest](../../models/components/replacescheduleintervalsrequest.md) | :heavy_check_mark:                                                                                       | N/A                                                                                                      |
| `opts`                                                                                                   | [][operations.Option](../../models/operations/option.md)                                                 | :heavy_minus_sign:                                                                                       | The options for this request.                                                                            |

### Response

**[*operations.ReplaceScheduleIntervalsResponse](../../models/operations/replacescheduleintervalsresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404, 409           | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## ListScheduleInvoices

List the staged invoice projections for a schedule, newest period first.

### Example Usage

<!-- UsageSnippet language="go" operationID="listScheduleInvoices" method="get" path="/v0/billingSchedules/{id}/invoices" -->
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

    res, err := s.BillingSchedules.ListScheduleInvoices(ctx, "<id>")
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

**[*operations.ListScheduleInvoicesResponse](../../models/operations/listscheduleinvoicesresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## GenerateScheduleInvoices

Generate (or regenerate) staged invoice projections for a schedule from its current intervals. Idempotent — replaces any existing staged rows. Schedule must have at least one interval.

### Example Usage

<!-- UsageSnippet language="go" operationID="generateScheduleInvoices" method="post" path="/v0/billingSchedules/{id}/invoices" -->
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

    res, err := s.BillingSchedules.GenerateScheduleInvoices(ctx, "<id>")
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

**[*operations.GenerateScheduleInvoicesResponse](../../models/operations/generatescheduleinvoicesresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404, 409           | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |