# MeCredential

The credential of the call. clientId is set for an OAuth token and apiKeyId for an API key.


## Fields

| Field                                                                      | Type                                                                       | Required                                                                   | Description                                                                |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `Type`                                                                     | [components.MeCredentialType](../../models/components/mecredentialtype.md) | :heavy_check_mark:                                                         | N/A                                                                        |
| `ClientID`                                                                 | `*string`                                                                  | :heavy_minus_sign:                                                         | The OAuth client of the token.                                             |
| `APIKeyID`                                                                 | `*string`                                                                  | :heavy_minus_sign:                                                         | The API key of the call.                                                   |