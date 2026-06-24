# InvoicesV2

## Overview

Invoice V2 operations supporting billing cycles organized by time periods. Warning: v0 invoice endpoints are no longer supported.

### Available Operations

* [List](#list) - List
* [ListLineItems](#listlineitems) - List Line Items
* [CreateLineItem](#createlineitem) - Create Manual Line Item
* [Get](#get) - Get
* [GetLineItems](#getlineitems) - Get Line Items
* [CreateInvoiceRefund](#createinvoicerefund) - Refund Invoice
* [ListInvoiceRefunds](#listinvoicerefunds) - List Invoice Refunds
* [VoidInvoiceRefund](#voidinvoicerefund) - Void Invoice Refund

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
	"log"
)

func main() {
    ctx := context.Background()

    s := paygentic.New(
        paygentic.WithSecurity(os.Getenv("PAYGENTIC_BEARER_AUTH")),
    )

    res, err := s.InvoicesV2.Get(ctx, "<id>", nil, paygentic.Pointer[int64](100), nil)
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                               | Type                                                                    | Required                                                                | Description                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `ctx`                                                                   | [context.Context](https://pkg.go.dev/context#Context)                   | :heavy_check_mark:                                                      | The context to use for the request.                                     |
| `id`                                                                    | `string`                                                                | :heavy_check_mark:                                                      | The invoice ID                                                          |
| `expand`                                                                | `*string`                                                               | :heavy_minus_sign:                                                      | Comma-separated list of fields to expand. Currently supports: lineItems |
| `lineItemsLimit`                                                        | `*int64`                                                                | :heavy_minus_sign:                                                      | Page size for line items when expand=lineItems                          |
| `lineItemsPageToken`                                                    | `*string`                                                               | :heavy_minus_sign:                                                      | Pagination token for line items when expand=lineItems                   |
| `opts`                                                                  | [][operations.Option](../../models/operations/option.md)                | :heavy_minus_sign:                                                      | The options for this request.                                           |

### Response

**[*components.Invoice](../../models/components/invoice.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 403, 404                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## GetLineItems

Get paginated line items for an invoice from the analytics service

### Example Usage

<!-- UsageSnippet language="go" operationID="getInvoiceLineItems" method="get" path="/v2/invoices/{id}/lineItems" -->
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

    res, err := s.InvoicesV2.GetLineItems(ctx, "<id>", paygentic.Pointer[int64](100), nil)
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
| `limit`                                                  | `*int64`                                                 | :heavy_minus_sign:                                       | Maximum number of line items to return                   |
| `pageToken`                                              | `*string`                                                | :heavy_minus_sign:                                       | Token for pagination to fetch the next page of results   |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*components.InvoiceLineItemsResponse](../../models/components/invoicelineitemsresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 403, 404                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

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