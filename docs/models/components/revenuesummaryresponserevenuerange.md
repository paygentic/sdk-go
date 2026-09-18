# RevenueSummaryResponseRevenueRange

Where the caller's revenue actually lies in time. Scoped by the same filters as the request (merchant, and where given customer, subscription and currency), so it is not an account-wide statement. Present only when the selected range returned nothing. An object carries the bounds of the real revenue; null means no revenue under these filters at any time; an absent field means the extent was not resolved, because the result was not empty or because the lookup failed. An absent field must never be read as an absence. The bounds may span more than this endpoint's maximum queryable range, so clamp before re-querying.


## Fields

| Field                                     | Type                                      | Required                                  | Description                               |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| `From`                                    | [time.Time](https://pkg.go.dev/time#Time) | :heavy_check_mark:                        | Earliest invoice issue instant.           |
| `To`                                      | [time.Time](https://pkg.go.dev/time#Time) | :heavy_check_mark:                        | Latest invoice issue instant.             |