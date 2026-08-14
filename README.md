# Shopping Cart - Miva Merchant Payment Modules

Easy to install payment modules for Miva Merchant.
These packages post card-not-present authorizations to PlugnPay Remote API (`pnpremote.cgi`). Card data is collected on the merchant storefront.

Miva Merchant **v2.x** and **v4.x** modules are retired and no longer offered in this repository.

| Folder | Target | Notes |
|---|---|---|
| [Miva_v26.x](./Miva_v26.x/) | **Miva 26.x** (26R1/26R2) | **Beta** — modern Module API 10.00, `MvCALL`, no commerce DLL |

## Downloads by Miva Merchant version

### Miva Merchant v26.x (beta — 26R1 / 26R2)

* **Remote API (Beta)** — onsite card collection via `pnpremote.cgi`
  - [Download](./Miva_v26.x/miva_26_api_module.zip)
  - Source: [./Miva_v26.x/src/plugnpayapi.mv](./Miva_v26.x/src/plugnpayapi.mv)
  - Docs: [package README](./Miva_v26.x/README.md) · [INSTALL.txt](./Miva_v26.x/INSTALL.txt) · [module README](./Miva_v26.x/src/README.md)

Package overview: [./Miva_v26.x/README.md](./Miva_v26.x/README.md)

## Installation

For complete instructions, open the README inside the package folder (or the linked docs above).

### Miva Merchant 26.x — Remote API

1. Download [miva_26_api_module.zip](./Miva_v26.x/miva_26_api_module.zip).
2. Compile `plugnpayapi.mv` → `plugnpayapi.mvc`.
3. Upload under Domain Settings → Modules; enable and configure Publisher Name / Remote Client Password.
4. Test checkout (`authonly` by default; capture in PlugnPay Admin).

- Quick install: [Miva_v26.x/INSTALL.txt](./Miva_v26.x/INSTALL.txt)

## Usage

### Remote API (Miva 26.x)

* Checkout collects payment data on the Miva storefront (increases PCI scope).
* Module posts to `https://pay1.plugnpay.com/payment/pnpremote.cgi` via HTTPS `MvCALL`.
* Default `authtype=authonly`; optional `authpostauth` (sale).
* `client=miva_remoteapi`.
* Capture / void / refund in PlugnPay Merchant Admin (not from Miva Admin in v1).
* Compile `.mv` → `.mvc` before uploading to a 26.x domain.

## Repository layout

```
shopping-cart-Miva/
  README.md
  Miva_v26.x/                     # beta (Merchant 26.x) — Remote API
    README.md
    INSTALL.txt
    miva_26_api_module.zip
    src/plugnpayapi.mv
```

## Support

Provided AS IS. See [PlugnPay docs](https://docs.plugnpay.com/) and the module README for integration details.
