# InvoicesV2

## Overview

Invoice V2 operations supporting billing cycles organized by time periods. Warning: v0 invoice endpoints are no longer supported.

### Available Operations

* [List](#list) - List
* [ListLineItems](#listlineitems) - List Line Items
* [CreateLineItem](#createlineitem) - Create Manual Line Item
* [ListProjectedInvoices](#listprojectedinvoices) - List projected
* [Get](#get) - Get
* [GetLineItems](#getlineitems) - Get Line Items
* [DownloadInvoicePdf](#downloadinvoicepdf) - Download Invoice PDF
* [RecordInvoicePayment](#recordinvoicepayment) - Settle Invoice Payment
* [CreateInvoiceRefund](#createinvoicerefund) - Refund Invoice
* [ListInvoiceRefunds](#listinvoicerefunds) - List Invoice Refunds
* [VoidInvoiceRefund](#voidinvoicerefund) - Void Invoice Refund
* [RetryInvoicePayment](#retryinvoicepayment) - Retry Payment

## List

List invoices with optional filters. Platform users can use nextActionAt=ready to get invoices ready for processing.

### Example Usage

<!-- UsageSnippet language="go" operationID="listInvoices" method="get" path="/v2/invoices" -->
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

    res, err := s.InvoicesV2.List(ctx, &operations.ListInvoicesRequest{})
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                        | Type                                                                             | Required                                                                         | Description                                                                      |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `ctx`                                                                            | [context.Context](https://pkg.go.dev/context#Context)                            | :heavy_check_mark:                                                               | The context to use for the request.                                              |
| `request`                                                                        | [operations.ListInvoicesRequest](../../models/operations/listinvoicesrequest.md) | :heavy_check_mark:                                                               | The request object to use for the request.                                       |
| `opts`                                                                           | [][operations.Option](../../models/operations/option.md)                         | :heavy_minus_sign:                                                               | The options for this request.                                                    |

### Response

**[*operations.ListInvoicesResponse](../../models/operations/listinvoicesresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 403                          | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## ListLineItems

List pending and invoiced line items for a subscription from the billing database. Returns exact fee amounts and estimated metered charges.

### Example Usage

<!-- UsageSnippet language="go" operationID="listLineItems" method="get" path="/v2/invoices/lineItems" -->
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

    res, err := s.InvoicesV2.ListLineItems(ctx, &operations.ListLineItemsRequest{})
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
| `request`                                                                          | [operations.ListLineItemsRequest](../../models/operations/listlineitemsrequest.md) | :heavy_check_mark:                                                                 | The request object to use for the request.                                         |
| `opts`                                                                             | [][operations.Option](../../models/operations/option.md)                           | :heavy_minus_sign:                                                                 | The options for this request.                                                      |

### Response

**[*components.LineItemsResponse](../../models/components/lineitemsresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## CreateLineItem

Create a manual line item for a billing v1 subscription. Manual line items are ad-hoc charges or credits that flow through the same collection pipeline as auto-generated items. Exactly one of subscriptionId or invoiceId must be provided.

### Example Usage

<!-- UsageSnippet language="go" operationID="createLineItem" method="post" path="/v2/invoices/lineItems" -->
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

    res, err := s.InvoicesV2.CreateLineItem(ctx, components.CreateManualLineItemRequest{
        DisplayName: "Nathan54",
        Currency: "Rwanda Franc",
        Quantity: 6214.31,
        UnitPrice: 7408.13,
    }, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                       | Type                                                                                                            | Required                                                                                                        | Description                                                                                                     |
| --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                           | [context.Context](https://pkg.go.dev/context#Context)                                                           | :heavy_check_mark:                                                                                              | The context to use for the request.                                                                             |
| `body`                                                                                                          | [components.CreateManualLineItemRequest](../../models/components/createmanuallineitemrequest.md)                | :heavy_check_mark:                                                                                              | N/A                                                                                                             |
| `idempotencyKey`                                                                                                | `*string`                                                                                                       | :heavy_minus_sign:                                                                                              | Optional idempotency key. If provided, duplicate requests with the same key return the previously created item. |
| `opts`                                                                                                          | [][operations.Option](../../models/operations/option.md)                                                        | :heavy_minus_sign:                                                                                              | The options for this request.                                                                                   |

### Response

**[*components.LineItem](../../models/components/lineitem.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404, 409, 422      | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## ListProjectedInvoices

List the invoices a subscription will issue in a range of invoice moments, one projected invoice for each distinct invoice moment. Projected invoices are derived on each read and never stored. Each has status PROJECTED, and its id is stable between reads, but GET /v2/invoices/{id} returns 404 for it. Totals EXCLUDE usage: metered charges are not projected, and an invoice moment that has only metered charges is omitted. Tax and sequenceNumber are estimates. The range filters on the invoice moment (invoiceAt) in [from, to). A from before now is treated as now. to must be after from and at most one year after now; now is the subscription's test-clock time when it has a test clock. A terminated subscription returns an empty list. Each invoice carries its lines in lineItems. Authorization is the same as listing invoices.

### Example Usage

<!-- UsageSnippet language="go" operationID="listProjectedInvoices" method="get" path="/v2/invoices/projected" -->
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

    res, err := s.InvoicesV2.ListProjectedInvoices(ctx, operations.ListProjectedInvoicesRequest{
        SubscriptionID: "<id>",
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
| `request`                                                                                          | [operations.ListProjectedInvoicesRequest](../../models/operations/listprojectedinvoicesrequest.md) | :heavy_check_mark:                                                                                 | The request object to use for the request.                                                         |
| `opts`                                                                                             | [][operations.Option](../../models/operations/option.md)                                           | :heavy_minus_sign:                                                                                 | The options for this request.                                                                      |

### Response

**[*operations.ListProjectedInvoicesResponse](../../models/operations/listprojectedinvoicesresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 403, 404                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## Get

Retrieve a single invoice with real-time aggregates (for ACTIVE/CLOSING/CLOSED) or cached aggregates (for finalized invoices). Optionally include line items with expand=lineItems.

### Example Usage

<!-- UsageSnippet language="go" operationID="getInvoice" method="get" path="/v2/invoices/{id}" -->
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

    res, err := s.InvoicesV2.Get(ctx, operations.GetInvoiceRequest{
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

| Parameter                                                                    | Type                                                                         | Required                                                                     | Description                                                                  |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `ctx`                                                                        | [context.Context](https://pkg.go.dev/context#Context)                        | :heavy_check_mark:                                                           | The context to use for the request.                                          |
| `request`                                                                    | [operations.GetInvoiceRequest](../../models/operations/getinvoicerequest.md) | :heavy_check_mark:                                                           | The request object to use for the request.                                   |
| `opts`                                                                       | [][operations.Option](../../models/operations/option.md)                     | :heavy_minus_sign:                                                           | The options for this request.                                                |

### Response

**[*components.Invoice](../../models/components/invoice.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 403, 404                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## GetLineItems

Get paginated line items for an invoice

### Example Usage

<!-- UsageSnippet language="go" operationID="getInvoiceLineItems" method="get" path="/v2/invoices/{id}/lineItems" -->
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

    res, err := s.InvoicesV2.GetLineItems(ctx, operations.GetInvoiceLineItemsRequest{
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

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `ctx`                                                                                          | [context.Context](https://pkg.go.dev/context#Context)                                          | :heavy_check_mark:                                                                             | The context to use for the request.                                                            |
| `request`                                                                                      | [operations.GetInvoiceLineItemsRequest](../../models/operations/getinvoicelineitemsrequest.md) | :heavy_check_mark:                                                                             | The request object to use for the request.                                                     |
| `opts`                                                                                         | [][operations.Option](../../models/operations/option.md)                                       | :heavy_minus_sign:                                                                             | The options for this request.                                                                  |

### Response

**[*components.InvoiceLineItemsResponse](../../models/components/invoicelineitemsresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 403, 404                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## DownloadInvoicePdf

Downloads the Paygentic-rendered invoice document. The caller must be authenticated and entitled to the invoice; the stored document is streamed back, so no storage URL is ever handed out. Returns 404 when the invoice's document is the tax provider's rather than ours — in that case the invoice resource reports pdfSource `tax_provider` and its pdfUrl points at the provider's link instead.

### Example Usage

<!-- UsageSnippet language="go" operationID="downloadInvoicePdf" method="get" path="/v2/invoices/{id}/pdf" -->
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

    res, err := s.InvoicesV2.DownloadInvoicePdf(ctx, "<id>")
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
| `id`                                                     | `string`                                                 | :heavy_check_mark:                                       | The invoice ID                                           |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[io.ReadCloser](../../.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## RecordInvoicePayment

Settle an unpaid invoice in status `ISSUED` or `PAYMENT_FAILED`. The `method` field selects how.

- `hosted_link`: create a new hosted payment link and email it to the customer. The invoice stays unpaid until the customer pays on the link. Each call replaces the previous link. A payment link expires after 30 days; to collect an invoice whose link has expired, call this method again.
- `out_of_band`: record a payment that you collected outside Paygentic. The invoice changes to `PAID` immediately. A second call returns 409.

For `hosted_link`, an invoice that does not exist returns 404, the same as an invoice of another merchant.

Paygentic selects the payment provider from your connected payment account. The response reports the provider.

**Warning:** each `hosted_link` call creates a new link and sends the customer a new email. Do not retry a `hosted_link` call after a timeout: first read the invoice to see if a new link exists.

### Example Usage

<!-- UsageSnippet language="go" operationID="recordInvoicePayment" method="post" path="/v2/invoices/{id}/payment" -->
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

    res, err := s.InvoicesV2.RecordInvoicePayment(ctx, "<id>", operations.RecordInvoicePaymentRequestBody{
        Method: components.InvoicePaymentMethodHostedLink,
    })
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        switch res.Type {
            case operations.RecordInvoicePaymentResponseTypeOutOfBand:
                // res.OutOfBandPaymentResult is populated
            case operations.RecordInvoicePaymentResponseTypeHostedLink:
                // res.HostedLinkPaymentResult is populated
            default:
                // Unknown type - use res.GetUnknownRaw() for raw JSON
        }

    }
}
```

### Parameters

| Parameter                                                                                                | Type                                                                                                     | Required                                                                                                 | Description                                                                                              |
| -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                    | [context.Context](https://pkg.go.dev/context#Context)                                                    | :heavy_check_mark:                                                                                       | The context to use for the request.                                                                      |
| `id`                                                                                                     | `string`                                                                                                 | :heavy_check_mark:                                                                                       | The invoice ID                                                                                           |
| `body`                                                                                                   | [operations.RecordInvoicePaymentRequestBody](../../models/operations/recordinvoicepaymentrequestbody.md) | :heavy_check_mark:                                                                                       | N/A                                                                                                      |
| `opts`                                                                                                   | [][operations.Option](../../models/operations/option.md)                                                 | :heavy_minus_sign:                                                                                       | The options for this request.                                                                            |

### Response

**[*operations.RecordInvoicePaymentResponse](../../models/operations/recordinvoicepaymentresponse.md), error**

### Errors

| Error Type                      | Status Code                     | Content Type                    |
| ------------------------------- | ------------------------------- | ------------------------------- |
| errors.BadRequest               | 400                             | application/json                |
| errors.Error                    | 403, 404, 409                   | application/json                |
| errors.UnprocessableEntityError | 422                             | application/json                |
| errors.Error                    | 500                             | application/json                |
| errors.PaygenticDefaultError    | 4XX, 5XX                        | \*/\*                           |

## CreateInvoiceRefund

Issue a full refund against a paid invoice by creating a credit note. The invoice stays PAID; the refund is recorded as a child credit note. Accessible to the owning merchant or platform operators. Only works for invoices in PAID status that have not already been refunded. Full refund only — the entire invoice (subtotal + tax) is credited.

### Example Usage

<!-- UsageSnippet language="go" operationID="createInvoiceRefund" method="post" path="/v2/invoices/{id}/refunds" -->
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

    res, err := s.InvoicesV2.CreateInvoiceRefund(ctx, "<id>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                               | Type                                                                                                    | Required                                                                                                | Description                                                                                             |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                   | [context.Context](https://pkg.go.dev/context#Context)                                                   | :heavy_check_mark:                                                                                      | The context to use for the request.                                                                     |
| `id`                                                                                                    | `string`                                                                                                | :heavy_check_mark:                                                                                      | The invoice ID                                                                                          |
| `body`                                                                                                  | [*operations.CreateInvoiceRefundRequestBody](../../models/operations/createinvoicerefundrequestbody.md) | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `opts`                                                                                                  | [][operations.Option](../../models/operations/option.md)                                                | :heavy_minus_sign:                                                                                      | The options for this request.                                                                           |

### Response

**[*components.InvoiceRefund](../../models/components/invoicerefund.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 403, 404                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## ListInvoiceRefunds

List the credit notes (refunds) recorded against an invoice. Accessible to the owning merchant or platform operators.

### Example Usage

<!-- UsageSnippet language="go" operationID="listInvoiceRefunds" method="get" path="/v2/invoices/{id}/refunds" -->
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

    res, err := s.InvoicesV2.ListInvoiceRefunds(ctx, "<id>")
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
| `id`                                                     | `string`                                                 | :heavy_check_mark:                                       | The invoice ID                                           |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*components.InvoiceRefundList](../../models/components/invoicerefundlist.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 403, 404                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## VoidInvoiceRefund

Void a previously-issued refund (credit note). Reverses the credit note in the tax provider and excludes it from revenue. Accessible to the owning merchant or platform operators.

### Example Usage

<!-- UsageSnippet language="go" operationID="voidInvoiceRefund" method="post" path="/v2/invoices/{id}/refunds/{refundId}/void" -->
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

    res, err := s.InvoicesV2.VoidInvoiceRefund(ctx, "<id>", "<id>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                           | Type                                                                                                | Required                                                                                            | Description                                                                                         |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                               | [context.Context](https://pkg.go.dev/context#Context)                                               | :heavy_check_mark:                                                                                  | The context to use for the request.                                                                 |
| `id`                                                                                                | `string`                                                                                            | :heavy_check_mark:                                                                                  | The invoice ID                                                                                      |
| `refundID`                                                                                          | `string`                                                                                            | :heavy_check_mark:                                                                                  | The refund (credit note) ID                                                                         |
| `body`                                                                                              | [*operations.VoidInvoiceRefundRequestBody](../../models/operations/voidinvoicerefundrequestbody.md) | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `opts`                                                                                              | [][operations.Option](../../models/operations/option.md)                                            | :heavy_minus_sign:                                                                                  | The options for this request.                                                                       |

### Response

**[*components.InvoiceRefund](../../models/components/invoicerefund.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 403, 404                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## RetryInvoicePayment

Charge the customer's saved payment method again for an unpaid invoice.

The invoice must be in status `ISSUED` or `PAYMENT_FAILED`, auto-charge must be on for its subscription, and the invoice must have a payment session. If not, the response is 400.

The response status tells you the result. Only 200 means that the charge succeeded. Every other response from this operation that has a `retry_payment_result` body has `success: false`, and `error.code` gives the reason:

| Status | `error.code` | Meaning |
| --- | --- | --- |
| 200 | — | The charge succeeded, the provider had already collected it, or no amount is unpaid. |
| 202 | `processing` | The provider accepted the charge. It settles later (for example, a bank debit). |
| 402 | a decline code, for example `card_declined`, `insufficient_funds`, `do_not_honor`, `authentication_required` | The provider declined the payment method. |
| 409 | `concurrent_attempt` | Another payment attempt for this invoice is in progress. |
| 409 | `PAYMENT_SESSION_EXPIRED` | The payment link expired (after 30 days). Create a new link with `POST /v2/invoices/{id}/payment` and `method: hosted_link`, then retry. If the customer also has no usable saved payment method, the response is 422 instead. |
| 409 | another value, or no `code` | The payment session cannot be charged in its current state (for example `session_unusable`, `non_confirmable`, `PAYMENT_PROCESSING`, `PAYMENT_ALREADY_COMPLETED`). Read `error.message` for the cause. |
| 422 | `no_payment_method` | The customer has no usable saved payment method. Send a payment link instead. |
| 502 | `provider_unavailable` or none | The payment provider did not answer, or the provider failed the charge for a reason that is not known. Retry later. |

A 500 response has the standard error body, not `retry_payment_result`. It is an internal error, and a retry does not fix it.

An invoice that does not exist returns 404, the same as an invoice of another merchant.

This operation is rate limited to one call each minute for each invoice.

### Example Usage

<!-- UsageSnippet language="go" operationID="retryInvoicePayment" method="post" path="/v2/invoices/{id}/retryPayment" -->
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

    res, err := s.InvoicesV2.RetryInvoicePayment(ctx, "<id>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                               | Type                                                                                                    | Required                                                                                                | Description                                                                                             |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                   | [context.Context](https://pkg.go.dev/context#Context)                                                   | :heavy_check_mark:                                                                                      | The context to use for the request.                                                                     |
| `id`                                                                                                    | `string`                                                                                                | :heavy_check_mark:                                                                                      | The invoice ID                                                                                          |
| `body`                                                                                                  | [*operations.RetryInvoicePaymentRequestBody](../../models/operations/retryinvoicepaymentrequestbody.md) | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `opts`                                                                                                  | [][operations.Option](../../models/operations/option.md)                                                | :heavy_minus_sign:                                                                                      | The options for this request.                                                                           |

### Response

**[*components.RetryPaymentResponse](../../models/components/retrypaymentresponse.md), error**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| errors.BadRequest                | 400                              | application/json                 |
| errors.RetryPaymentResponseError | 402, 409, 422                    | application/json                 |
| errors.Error                     | 403, 429                         | application/json                 |
| errors.Error                     | 500                              | application/json                 |
| errors.RetryPaymentResponseError | 502                              | application/json                 |
| errors.PaygenticDefaultError     | 4XX, 5XX                         | \*/\*                            |