# Me

## Overview

The caller: who it is in its active organization and what it can do

### Available Operations

* [GetMe](#getme) - Get the caller

## GetMe

Returns the caller's identity in its active organization, its roles, and the permissions that its credential holds there. The permissions are the effective set for the credential of the call: for a session or an API key, those of the principal; for an OAuth token, those of the principal narrowed to the scopes of the token.

### Example Usage

<!-- UsageSnippet language="go" operationID="getMe" method="get" path="/v0/me" -->
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

    res, err := s.Me.GetMe(ctx)
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
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*components.Me](../../models/components/me.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 401, 403                     | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |