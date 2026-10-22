# AuthorizationDenialReason

Present on a 403 from the authorization check. Says why access was refused: the caller has no role that grants the permission, the OAuth token lacks the scope, or the caller is not a member of the organization.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.AuthorizationDenialReasonNoPermission

// Open enum: custom values can be created with a direct type cast
custom := components.AuthorizationDenialReason("custom_value")
```


## Values

| Name                                         | Value                                        |
| -------------------------------------------- | -------------------------------------------- |
| `AuthorizationDenialReasonNoPermission`      | no_permission                                |
| `AuthorizationDenialReasonInsufficientScope` | insufficient_scope                           |
| `AuthorizationDenialReasonNotMember`         | not_member                                   |