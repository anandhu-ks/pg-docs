## Payment URL Structure
```
https://payments.open.money/open/redirect/layer/{brand_color}/{error_color}/{brand_logo}?redirect_url={url}
```

### Parameters
| Parameter       | Type   | Description |
|---------------|--------|-------------|
| `brand_color`   | String | Hex code for the brand color (without #) |
| `error_color`   | String | Hex code for the error color (without #) |
| `brand_logo`    | String | Base64-encoded URL of the brand logo or `null` |
| `redirect_url`  | String | URL to which the user is redirected after payment |

### Example Payment URL
```
https://payments.open.money/open/redirect/layer/00FF00/FF0000/null?redirect_url=https://app.open.money
```

## Handling Payment Response
After payment, the user is redirected to the `redirect_url` with a `payment_res` parameter containing a Base64-encoded JSON object.

### Example Redirect URL After Payment
```
https://app.open.money/login?payment_res=eyJwYXltZW50X3Rva2VuIjoicHRfMmI2N2FEODQzQjI1MjA1IiwicGF5bWVudF9pZCI6InB5X2FjNjdBZDg1M2E0MGFCMyIsInN0YXR1cyI6InN1Y2Nlc3MifQ%3D%3D
```

### Decoded `payment_res` Example
```json
{
  "payment_token": "pt_2b67aD843B25205",
  "payment_id": "py_ac67Ad853a40aB3",
  "status": "success"
}
```

