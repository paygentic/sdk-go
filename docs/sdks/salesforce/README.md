# Salesforce

## Overview

### Available Operations

* [ListSalesforceAccounts](#listsalesforceaccounts) - List Salesforce accounts

## ListSalesforceAccounts

Returns Accounts from the merchant's connected Salesforce org via live proxy SOQL.

### Example Usage

<!-- UsageSnippet language="go" operationID="listSalesforceAccounts" method="get" path="/v0/integrations/salesforce/accounts" -->
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

    res, err := s.Salesforce.ListSalesforceAccounts(ctx, "<id>", nil, paygentic.Pointer[int64](50), paygentic.Pointer[int64](0))
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
| `merchantID`                                             | `string`                                                 | :heavy_check_mark:                                       | Merchant whose Salesforce connection to use.             |
| `q`                                                      | `*string`                                                | :heavy_minus_sign:                                       | Optional name filter (LIKE match).                       |
| `limit`                                                  | `*int64`                                                 | :heavy_minus_sign:                                       | N/A                                                      |
| `offset`                                                 | `*int64`                                                 | :heavy_minus_sign:                                       | N/A                                                      |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.ListSalesforceAccountsResponse](../../models/operations/listsalesforceaccountsresponse.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403                     | application/json             |
| errors.Error                 | 500                          | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |