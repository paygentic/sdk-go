# Permission

A permission of the catalog: a resource read or write, or a sensitive action.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.PermissionOrganizationRead

// Open enum: custom values can be created with a direct type cast
custom := components.Permission("custom_value")
```


## Values

| Name                                         | Value                                        |
| -------------------------------------------- | -------------------------------------------- |
| `PermissionOrganizationRead`                 | organization:read                            |
| `PermissionMembersRead`                      | members:read                                 |
| `PermissionProfileRead`                      | profile:read                                 |
| `PermissionAPIKeysRead`                      | apiKeys:read                                 |
| `PermissionMerchantsRead`                    | merchants:read                               |
| `PermissionConsumersRead`                    | consumers:read                               |
| `PermissionCustomersRead`                    | customers:read                               |
| `PermissionPlansRead`                        | plans:read                                   |
| `PermissionPricesRead`                       | prices:read                                  |
| `PermissionProductsRead`                     | products:read                                |
| `PermissionFeaturesRead`                     | features:read                                |
| `PermissionFeesRead`                         | fees:read                                    |
| `PermissionBillableMetricsRead`              | billableMetrics:read                         |
| `PermissionItemsRead`                        | items:read                                   |
| `PermissionPricingUnitsRead`                 | pricingUnits:read                            |
| `PermissionSubscriptionsRead`                | subscriptions:read                           |
| `PermissionSubscriptionAdjustmentsRead`      | subscriptionAdjustments:read                 |
| `PermissionDiscountsRead`                    | discounts:read                               |
| `PermissionGrantsRead`                       | grants:read                                  |
| `PermissionEntitlementsRead`                 | entitlements:read                            |
| `PermissionCreditPoolsRead`                  | creditPools:read                             |
| `PermissionOrdersRead`                       | orders:read                                  |
| `PermissionBillingSchedulesRead`             | billingSchedules:read                        |
| `PermissionInvoicesRead`                     | invoices:read                                |
| `PermissionPaymentsRead`                     | payments:read                                |
| `PermissionPaymentSessionsRead`              | paymentSessions:read                         |
| `PermissionPortalSessionsRead`               | portalSessions:read                          |
| `PermissionPlatformUsersRead`                | platformUsers:read                           |
| `PermissionPlatformAdminRead`                | platformAdmin:read                           |
| `PermissionOrganizationCreationRead`         | organizationCreation:read                    |
| `PermissionComplianceRead`                   | compliance:read                              |
| `PermissionTaxSettingsRead`                  | taxSettings:read                             |
| `PermissionCostsRead`                        | costs:read                                   |
| `PermissionPaymentAccountsRead`              | paymentAccounts:read                         |
| `PermissionPayoutsRead`                      | payouts:read                                 |
| `PermissionExternalAccountsRead`             | externalAccounts:read                        |
| `PermissionExternalReferencesRead`           | externalReferences:read                      |
| `PermissionMerchantIntegrationsRead`         | merchantIntegrations:read                    |
| `PermissionWebhooksRead`                     | webhooks:read                                |
| `PermissionTestClocksRead`                   | testClocks:read                              |
| `PermissionApprovalsRead`                    | approvals:read                               |
| `PermissionSourcesRead`                      | sources:read                                 |
| `PermissionRevenueRead`                      | revenue:read                                 |
| `PermissionOrganizationWrite`                | organization:write                           |
| `PermissionMembersWrite`                     | members:write                                |
| `PermissionProfileWrite`                     | profile:write                                |
| `PermissionAPIKeysWrite`                     | apiKeys:write                                |
| `PermissionMerchantsWrite`                   | merchants:write                              |
| `PermissionConsumersWrite`                   | consumers:write                              |
| `PermissionCustomersWrite`                   | customers:write                              |
| `PermissionPlansWrite`                       | plans:write                                  |
| `PermissionPricesWrite`                      | prices:write                                 |
| `PermissionProductsWrite`                    | products:write                               |
| `PermissionFeaturesWrite`                    | features:write                               |
| `PermissionFeesWrite`                        | fees:write                                   |
| `PermissionBillableMetricsWrite`             | billableMetrics:write                        |
| `PermissionItemsWrite`                       | items:write                                  |
| `PermissionPricingUnitsWrite`                | pricingUnits:write                           |
| `PermissionSubscriptionsWrite`               | subscriptions:write                          |
| `PermissionSubscriptionAdjustmentsWrite`     | subscriptionAdjustments:write                |
| `PermissionDiscountsWrite`                   | discounts:write                              |
| `PermissionGrantsWrite`                      | grants:write                                 |
| `PermissionEntitlementsWrite`                | entitlements:write                           |
| `PermissionCreditPoolsWrite`                 | creditPools:write                            |
| `PermissionOrdersWrite`                      | orders:write                                 |
| `PermissionBillingSchedulesWrite`            | billingSchedules:write                       |
| `PermissionInvoicesWrite`                    | invoices:write                               |
| `PermissionPaymentsWrite`                    | payments:write                               |
| `PermissionPaymentSessionsWrite`             | paymentSessions:write                        |
| `PermissionPortalSessionsWrite`              | portalSessions:write                         |
| `PermissionPlatformUsersWrite`               | platformUsers:write                          |
| `PermissionPlatformAdminWrite`               | platformAdmin:write                          |
| `PermissionOrganizationCreationWrite`        | organizationCreation:write                   |
| `PermissionComplianceWrite`                  | compliance:write                             |
| `PermissionTaxSettingsWrite`                 | taxSettings:write                            |
| `PermissionCostsWrite`                       | costs:write                                  |
| `PermissionPaymentAccountsWrite`             | paymentAccounts:write                        |
| `PermissionPayoutsWrite`                     | payouts:write                                |
| `PermissionExternalAccountsWrite`            | externalAccounts:write                       |
| `PermissionExternalReferencesWrite`          | externalReferences:write                     |
| `PermissionMerchantIntegrationsWrite`        | merchantIntegrations:write                   |
| `PermissionWebhooksWrite`                    | webhooks:write                               |
| `PermissionTestClocksWrite`                  | testClocks:write                             |
| `PermissionApprovalsWrite`                   | approvals:write                              |
| `PermissionSourcesWrite`                     | sources:write                                |
| `PermissionEventsWrite`                      | events:write                                 |
| `PermissionInvoicesIssue`                    | invoices:issue                               |
| `PermissionInvoicesVoid`                     | invoices:void                                |
| `PermissionPaymentsRefund`                   | payments:refund                              |
| `PermissionOrganizationDelete`               | organization:delete                          |
| `PermissionOwnershipTransfer`                | ownership:transfer                           |
| `PermissionSubscriptionsTerminate`           | subscriptions:terminate                      |
| `PermissionSubscriptionsTerminateWithReason` | subscriptions:terminateWithReason            |
| `PermissionSubscriptionsReconcile`           | subscriptions:reconcile                      |
| `PermissionSubscriptionsUpdate`              | subscriptions:update                         |
| `PermissionSubscriptionsDelete`              | subscriptions:delete                         |
| `PermissionSubscriptionsTaxExempt`           | subscriptions:taxExempt                      |
| `PermissionSubscriptionsAutoApprove`         | subscriptions:autoApprove                    |
| `PermissionOrganizationResetData`            | organization:resetData                       |