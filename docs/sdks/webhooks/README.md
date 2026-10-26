# Webhooks

## Overview

Endpoints for setting up webhook integrations and administering webhook settings

### Available Operations

* [Get](#get) - Get
* [Enable](#enable) - Enable
* [Update](#update) - Update
* [Disable](#disable) - Disable
* [GetPortal](#getportal) - Get Portal Access

## Get

Returns the webhook configuration for your account. Returns 404 if webhooks have never been enabled.

### Example Usage

<!-- UsageSnippet language="go" operationID="getWebhooks" method="get" path="/v0/webhooks" -->
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

    res, err := s.Webhooks.Get(ctx, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                     | Type                                                                                                          | Required                                                                                                      | Description                                                                                                   |
| ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                         | [context.Context](https://pkg.go.dev/context#Context)                                                         | :heavy_check_mark:                                                                                            | The context to use for the request.                                                                           |
| `merchantID`                                                                                                  | `*string`                                                                                                     | :heavy_minus_sign:                                                                                            | The merchant organization ID. If omitted, defaults to the merchant associated with the authenticated API key. |
| `opts`                                                                                                        | [][operations.Option](../../models/operations/option.md)                                                      | :heavy_minus_sign:                                                                                            | The options for this request.                                                                                 |

### Response

**[*components.Webhooks](../../models/components/webhooks.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## Enable

Turns on webhook delivery for your account. Call it once: when a configuration already exists, enabled or disabled, the response is 400 with code `DUPLICATE_RESOURCE`. Use the update operation to turn delivery on or off after that. Endpoint URLs, event subscriptions and the signing secret are managed in the webhook portal.

### Example Usage

<!-- UsageSnippet language="go" operationID="createWebhooks" method="post" path="/v0/webhooks" -->
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

    res, err := s.Webhooks.Enable(ctx, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                     | Type                                                                                                          | Required                                                                                                      | Description                                                                                                   |
| ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                         | [context.Context](https://pkg.go.dev/context#Context)                                                         | :heavy_check_mark:                                                                                            | The context to use for the request.                                                                           |
| `merchantID`                                                                                                  | `*string`                                                                                                     | :heavy_minus_sign:                                                                                            | The merchant organization ID. If omitted, defaults to the merchant associated with the authenticated API key. |
| `opts`                                                                                                        | [][operations.Option](../../models/operations/option.md)                                                      | :heavy_minus_sign:                                                                                            | The options for this request.                                                                                 |

### Response

**[*components.Webhooks](../../models/components/webhooks.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## Update

Turns webhook delivery on or off. Set `enabled` to `false` to pause delivery and to `true` to resume it. Endpoints and their event subscriptions are kept. Returns 404 if webhooks have never been enabled.

### Example Usage

<!-- UsageSnippet language="go" operationID="updateWebhooks" method="patch" path="/v0/webhooks" -->
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

    res, err := s.Webhooks.Update(ctx, operations.UpdateWebhooksRequestBody{
        Enabled: true,
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

| Parameter                                                                                                     | Type                                                                                                          | Required                                                                                                      | Description                                                                                                   |
| ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                         | [context.Context](https://pkg.go.dev/context#Context)                                                         | :heavy_check_mark:                                                                                            | The context to use for the request.                                                                           |
| `body`                                                                                                        | [operations.UpdateWebhooksRequestBody](../../models/operations/updatewebhooksrequestbody.md)                  | :heavy_check_mark:                                                                                            | N/A                                                                                                           |
| `merchantID`                                                                                                  | `*string`                                                                                                     | :heavy_minus_sign:                                                                                            | The merchant organization ID. If omitted, defaults to the merchant associated with the authenticated API key. |
| `opts`                                                                                                        | [][operations.Option](../../models/operations/option.md)                                                      | :heavy_minus_sign:                                                                                            | The options for this request.                                                                                 |

### Response

**[*components.Webhooks](../../models/components/webhooks.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.BadRequest            | 400                          | application/json             |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## Disable

Pauses webhook delivery. This has the same effect as the update operation with `enabled: false`: it does not delete the configuration, the endpoints or their event subscriptions. Use the update operation with `enabled: true` to resume delivery. Returns 404 if webhooks have never been enabled.

### Example Usage

<!-- UsageSnippet language="go" operationID="deleteWebhooks" method="delete" path="/v0/webhooks" -->
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

    err := s.Webhooks.Disable(ctx, nil)
    if err != nil {
        log.Fatal(err)
    }
}
```

### Parameters

| Parameter                                                                                                     | Type                                                                                                          | Required                                                                                                      | Description                                                                                                   |
| ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                         | [context.Context](https://pkg.go.dev/context#Context)                                                         | :heavy_check_mark:                                                                                            | The context to use for the request.                                                                           |
| `merchantID`                                                                                                  | `*string`                                                                                                     | :heavy_minus_sign:                                                                                            | The merchant organization ID. If omitted, defaults to the merchant associated with the authenticated API key. |
| `opts`                                                                                                        | [][operations.Option](../../models/operations/option.md)                                                      | :heavy_minus_sign:                                                                                            | The options for this request.                                                                                 |

### Response

**error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |

## GetPortal

Returns a link to the webhook portal, where you add endpoints, choose event types, read the signing secret and inspect deliveries. The link opens without a login and expires one hour after it is issued, at `expiresAt`. Treat it as a secret. The link is read-only unless the caller holds `webhooks:write`: a read-only portal shows endpoints and deliveries but does not let you add or change endpoints, read the signing secret or replay messages. Returns 404 unless webhooks are enabled.

### Example Usage

<!-- UsageSnippet language="go" operationID="getWebhookPortal" method="get" path="/v0/webhooks/portal" -->
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

    res, err := s.Webhooks.GetPortal(ctx, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                     | Type                                                                                                          | Required                                                                                                      | Description                                                                                                   |
| ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                         | [context.Context](https://pkg.go.dev/context#Context)                                                         | :heavy_check_mark:                                                                                            | The context to use for the request.                                                                           |
| `merchantID`                                                                                                  | `*string`                                                                                                     | :heavy_minus_sign:                                                                                            | The merchant organization ID. If omitted, defaults to the merchant associated with the authenticated API key. |
| `opts`                                                                                                        | [][operations.Option](../../models/operations/option.md)                                                      | :heavy_minus_sign:                                                                                            | The options for this request.                                                                                 |

### Response

**[*components.WebhookPortal](../../models/components/webhookportal.md), error**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.Error                 | 401, 403, 404                | application/json             |
| errors.PaygenticDefaultError | 4XX, 5XX                     | \*/\*                        |