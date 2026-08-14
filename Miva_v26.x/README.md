# Miva Merchant v26.x — PlugnPay Payment Module

Package for **Miva Merchant 26.x** (26R1 / 26R2). Module API **10.00**.

## Choose a module

| | Remote API |
|---|---|
| Download | [miva_26_api_module.zip](./miva_26_api_module.zip) |
| Source | [src/plugnpayapi.mv](./src/plugnpayapi.mv) |
| Checkout | Onsite card fields → `pnpremote.cgi` |
| Card data on your server | Yes |
| Auth mode | `authonly` (default) or `authpostauth` |
| Status | **Beta** for Merchant 26.x |

## Remote API (onsite)

- Source: [src/](./src/)
- Download: [miva_26_api_module.zip](./miva_26_api_module.zip)
- Quick install: [INSTALL.txt](./INSTALL.txt)
- Module README: [src/README.md](./src/README.md)
- Module version: **1.0000** (beta)
- Declared `api_ver`: **10.00**

**Status: Beta.** Validate thoroughly on a 26.x store before production use.

Uses `PaymentModule_Runtime_Authorize` and HTTPS `MvCALL` (no commerce library). Capture / void / refund are performed in PlugnPay Merchant Admin.

### Requirements

- Miva Merchant **26.x**
- Compiled `plugnpayapi.mvc` (compile from `plugnpayapi.mv`)
- Storefront HTTPS
- PlugnPay Remote Client credentials

### Install steps

1. Download [miva_26_api_module.zip](./miva_26_api_module.zip) (or use `src/`).
2. Compile `plugnpayapi.mv` → `plugnpayapi.mvc`.
3. Upload under Domain Settings → Modules.
4. Configure Publisher Name, Remote Client Password, and Authorization Type.
5. Test checkout.

## Development layout

```
Miva_v26.x/
  README.md
  INSTALL.txt
  miva_26_api_module.zip
  src/
    plugnpayapi.mv
    README.md
```
