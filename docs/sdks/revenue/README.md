# Revenue

## Overview

Revenue data from invoices and payments

### Available Operations

* [Get](#get) - Get revenue summary
* [GetRevenueAccounts](#getrevenueaccounts) - List customer accounts

## Get

Returns revenue summary with invoice and payment breakdowns (outstanding/paid/writtenOff), plus a time-series trend. Revenue is what was billed in the period (by default, invoices issued in it; see periodBasis), whatever their status since, less refunds, both excluding tax; completed payments are reported under payments, never in revenue.

### Example Usage

<!-- UsageSnippet language="go" operationID="getRevenue" method="get" path="/v0/revenue" -->
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

    res, err := s.Revenue.Get(ctx, operations.GetRevenueRequest{
        StartTime: types.MustTimeFromString("2024-07-23T16:05:39.311Z"),
        EndTime: types.MustTimeFromString("2026-04-29T18:43:05.586Z"),
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

| Parameter                                                                    | Type                                                                         | Required                                                                     | Description                                                                  |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `ctx`                                                                        | [context.Context](https://pkg.go.dev/context#Context)                        | :heavy_check_mark:                                                           | The context to use for the request.                                          |
| `request`                                                                    | [operations.GetRevenueRequest](../../models/operations/getrevenuerequest.md) | :heavy_check_mark:                                                           | The request object to use for the request.                                   |
| `opts`                                                                       | [][operations.Option](../../models/operations/option.md)                     | :heavy_minus_sign:                                                           | The options for this request.                                                |

### Response

**[*components.RevenueSummaryResponse](../../models/components/revenuesummaryresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## GetRevenueAccounts

Returns each customer's account as at today, one row per customer and currency, with a total per currency. Every figure covers all dates: there is no date window.

`outstanding` is what customers owe: every invoice with status `ISSUED` or `PAYMENT_FAILED`, at the amount due printed on the invoice (subtotal and tax, each rounded to the currency's minor unit), so it is gross of tax. Revenue (`GET /v0/revenue`) is net of tax. `outstanding` splits into `awaitingPayment` (status `ISSUED`) and `paymentFailed` (status `PAYMENT_FAILED`, collection has ended); the two always add up to it, in count and amount. A credit invoice (a negative amount due) nets against what is owed and is counted in no `count`; nor is an invoice whose amount due rounds to zero. A customer with nothing counted and nothing owed has no row.

Amounts are grouped by currency and never combined or converted. `totals` covers every row in the filter, not only the returned page, so the rows on one page add up to `totals` only when the page holds every row. Pages fetched in separate requests are separate reads.

### Example Usage

<!-- UsageSnippet language="go" operationID="getRevenueAccounts" method="get" path="/v0/revenue/accounts" -->
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

    res, err := s.Revenue.GetRevenueAccounts(ctx, "<id>", nil, paygentic.Pointer[int64](50), paygentic.Pointer[int64](0))
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                                                                                                                            | Type                                                                                                                                                                                                                                 | Required                                                                                                                                                                                                                             | Description                                                                                                                                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                                                                                                                                                                | [context.Context](https://pkg.go.dev/context#Context)                                                                                                                                                                                | :heavy_check_mark:                                                                                                                                                                                                                   | The context to use for the request.                                                                                                                                                                                                  |
| `merchantID`                                                                                                                                                                                                                         | `string`                                                                                                                                                                                                                             | :heavy_check_mark:                                                                                                                                                                                                                   | Merchant whose customer accounts to report                                                                                                                                                                                           |
| `customerIds`                                                                                                                                                                                                                        | []`string`                                                                                                                                                                                                                           | :heavy_minus_sign:                                                                                                                                                                                                                   | Limit the rows and the totals to these customers of the merchant. A customer of another merchant, or one that does not exist, returns 404. A customer billed in several currencies has a row for each, so set `limit` to cover them. |
| `limit`                                                                                                                                                                                                                              | `*int64`                                                                                                                                                                                                                             | :heavy_minus_sign:                                                                                                                                                                                                                   | Number of rows to return                                                                                                                                                                                                             |
| `offset`                                                                                                                                                                                                                             | `*int64`                                                                                                                                                                                                                             | :heavy_minus_sign:                                                                                                                                                                                                                   | Number of rows to skip                                                                                                                                                                                                               |
| `opts`                                                                                                                                                                                                                               | [][operations.Option](../../models/operations/option.md)                                                                                                                                                                             | :heavy_minus_sign:                                                                                                                                                                                                                   | The options for this request.                                                                                                                                                                                                        |

### Response

**[*components.RevenueAccountsResponse](../../models/components/revenueaccountsresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |