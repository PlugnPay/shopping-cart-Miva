# PlugnPay Remote API Module for Miva Merchant 26.x

**Version:** 1.0.0 (**Beta**)  
**Target:** Miva Merchant **26.x** (26R1 / 26R2; Module API **10.00**)  
**Status:** Beta — validate on a 26.x store before production use.

Credit card payments via PlugnPay’s Remote API (`https://pay1.plugnpay.com/payment/pnpremote.cgi`).

Onsite card collection, `authonly` / `authpostauth`, HTTPS `MvCALL` (no commerce DLL), and no Miva-side Capture / Void / Refund.

## Features

- Onsite credit card collection (checkout stays on your Miva store)
- Authorize-only (`authonly`, default) or Sale (`authpostauth`)
- Modern Module API: `PaymentModule_Runtime_Authorize`, `vis_payment` settings
- HTTPS POST via `MvCALL` with `force_https, force_verify` (no `pnpmiva.so` / `.dll`)
- Optional CVV, publisher email notify, prevent gateway customer email (`dontsndmail`)
- Stores only safe order payment metadata (gateway order ID, auth code, AVS/CVV, last4)

Capture / void / refund are done in [PlugnPay Merchant Admin](https://pay1.plugnpay.com/admin/), matching other PlugnPay Remote API shopping-cart modules.

## PCI notice

This module collects cardholder data on your server, which increases PCI DSS scope.

## Requirements

- Miva Merchant **26.x** (Module API **10.00**; tested against the 26R1/26R2 line)
- Ability to **compile** `plugnpayapi.mv` → `plugnpayapi.mvc` (MivaScript Compiler / Empresa tooling)
- Outbound HTTPS from the Miva server to `pay1.plugnpay.com`
- Storefront **HTTPS**
- PlugnPay publisher-name (username)
- **Remote Client Password** (Security Administration — not the admin login password)

There is **no separate test host**. Test vs live is determined by the PlugnPay account credentials. Endpoint is always:

```text
https://pay1.plugnpay.com/payment/pnpremote.cgi
```

## Installation

See [../INSTALL.txt](../INSTALL.txt). Summary:

1. Compile `src/plugnpayapi.mv` to `plugnpayapi.mvc`.
2. Admin → Settings → Domain Settings → Modules → Add Module → upload `plugnpayapi.mvc`.
3. Assign / enable the module for the store; open Payment settings for **PlugnPay Remote API**.
4. Set Publisher Name, Remote Client Password, Authorization Type, CVV / email options.
5. Place a test order with your merchant credentials.

### Configuration reference

| Setting | Notes |
|---|---|
| Publisher Name | PlugnPay username → `publisher_name` |
| Remote Client Password | → `publisher_password` |
| Publisher Email | Optional → `publisher_email` / `notify_email` |
| Authorization Type | `authonly` (default) or `authpostauth` |
| Require CVV | Collect / send `card_cvv` |
| Prevent gateway customer email | Sends `dontsndmail=yes` |

**Authorization Type mapping**

- `authonly` → authorize only; Miva records OrderPayment type **1**; settle in PlugnPay Admin
- `authpostauth` → authorize and capture; Miva records OrderPayment type **5**

## Checkout flow

1. Customer enters card details on the Miva payment step.
2. `PaymentModule_Runtime_Authorize` POSTs underscore fields + `convert=underscores` to `pnpremote.cgi`.
3. On `FinalStatus=success` (or `success=yes`), an OrderPayment row is created and checkout continues.
4. On decline / error, the shopper sees the gateway message and remains in checkout.

`client` is sent as `miva_remoteapi`.

## File map

```
Miva_v26.x/
  README.md
  INSTALL.txt
  miva_26_api_module.zip
  src/
    plugnpayapi.mv
    README.md          # this file
```

## Support

Provided AS IS. See [PlugnPay docs](https://docs.plugnpay.com/) and the [Remote API specification](https://docs.plugnpay.com/docs/integration-specifications-documents/remote-api-integration-specification/).
