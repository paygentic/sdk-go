# PaymentSessions

## Overview

Handle payment session lifecycle and processing across various entity types including invoices and subscriptions

### Available Operations

* [ListPaymentSessions](#listpaymentsessions) - List

## ListPaymentSessions

List payment sessions for the authenticated merchant with optional filters. Supports filtering by subscriptionId, customerId, status, and entityType. When subscriptionId is provided the result includes both the subscription's own activation session (entityType='subscription') and any session attached to invoices for that subscription (entityType='invoice').

### Example Usage

<!-- UsageSnippet language="go" operationID="listPaymentSessions" method="get" path="/v0/paymentSessions" -->
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

    res, err := s.PaymentSessions.ListPaymentSessions(ctx, &operations.ListPaymentSessionsRequest{})
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
| `request`                                                                                      | [operations.ListPaymentSessionsRequest](../../models/operations/listpaymentsessionsrequest.md) | :heavy_check_mark:                                                                             | The request object to use for the request.                                                     |
| `opts`                                                                                         | [][operations.Option](../../models/operations/option.md)                                       | :heavy_minus_sign:                                                                             | The options for this request.                                                                  |

### Response

**[*operations.ListPaymentSessionsResponse](../../models/operations/listpaymentsessionsresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 401, 403                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |