# Merchants

## Overview

### Available Operations

* [Reset](#reset) - Reset a merchant's data

## Reset

With `scope: merchant`, deletes the merchant's customers and everything attached to them: subscriptions, invoices, line items, payments, entitlements, grants, orders, test clocks, usage events, invoice documents and, when tax is enabled, the documents in the merchant's Quaderno sandbox account. `keepCatalog: true` keeps the catalog (products, plans, prices, fees, features, billable metrics), and `keepCatalog: false` deletes it too; the merchant's configuration is always kept. With `scope: customer`, deletes one customer and what is attached to it; test clocks and the Quaderno account's documents are kept, since they belong to no single customer.

A `204` means every delete is done or scheduled: usage events and Quaderno documents finish in the background, and usage events still being ingested while it runs can survive it. A `502` means a store outside Postgres failed; the customers are already out of the API, and calling again with the same body finishes the reset. Calling again is always safe. While a customer waits for that, its external id is free for a new customer to take; a retry then deletes usage events by customer id only.

Not available in production.

### Example Usage

<!-- UsageSnippet language="go" operationID="resetMerchant" method="post" path="/v0/merchants/{merchantId}/reset" -->
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

    err := s.Merchants.Reset(ctx, "<id>", components.CreateMerchantResetMerchant(
        components.MerchantScope{
            KeepCatalog: false,
        },
    ))
    if err != nil {
        log.Fatal(err)
    }
}
```

### Parameters

| Parameter                                                            | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `ctx`                                                                | [context.Context](https://pkg.go.dev/context#Context)                | :heavy_check_mark:                                                   | The context to use for the request.                                  |
| `merchantID`                                                         | `string`                                                             | :heavy_check_mark:                                                   | N/A                                                                  |
| `body`                                                               | [components.MerchantReset](../../models/components/merchantreset.md) | :heavy_check_mark:                                                   | N/A                                                                  |
| `opts`                                                               | [][operations.Option](../../models/operations/option.md)             | :heavy_minus_sign:                                                   | The options for this request.                                        |

### Response

**error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403                     | application/json             |
| errors.Error                 | 500, 502                     | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |