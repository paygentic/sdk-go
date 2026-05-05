# Profitability

## Overview

Per-customer profitability summaries

### Available Operations

* [GetProfitability](#getprofitability) - Get profitability summary

## GetProfitability

Returns a per-customer profitability summary for a merchant over a date range. Each row aggregates revenue (from issued + paid invoices), cost (from metered cost discovery), profit, and margin. Customers are ranked by profit descending and capped at topN; the remainder is rolled into a single self-consistent 'Other' row whose revenue, cost, and profit reflect the same set of customers. Rows are inner-joined against the merchant's customer list, so orphaned meter subjects from deleted or unknown customers are dropped.

### Example Usage

<!-- UsageSnippet language="go" operationID="getProfitability" method="get" path="/v0/profitability" -->
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

    res, err := s.Profitability.GetProfitability(ctx, operations.GetProfitabilityRequest{
        MerchantID: "<id>",
        From: types.MustTimeFromString("2026-09-10T15:32:06.535Z"),
        To: types.MustTimeFromString("2026-10-20T08:45:45.521Z"),
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
| `request`                                                                                | [operations.GetProfitabilityRequest](../../models/operations/getprofitabilityrequest.md) | :heavy_check_mark:                                                                       | The request object to use for the request.                                               |
| `opts`                                                                                   | [][operations.Option](../../models/operations/option.md)                                 | :heavy_minus_sign:                                                                       | The options for this request.                                                            |

### Response

**[*components.ProfitabilitySummaryResponse](../../models/components/profitabilitysummaryresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |