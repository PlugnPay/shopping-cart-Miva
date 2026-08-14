# Miva Merchant v4.x — PlugnPay Payment Module

Packages for **Miva Merchant v4.x** (Windows NT). Source `plugnpay.mv` declares:

- Header: `Miva Merchant v4.x`
- `Module_API_Version`: **4.14**
- `Module_Version`: **4.2400**

Per the 2008 release notes: for Merchant **below 4.14** upload `plugnpay.mv`; for **4.14 and above** upload compiled `plugnpay.mvc`.

## Choose a package

| | Remote API (2008-03-13) | Remote API + commerce lib DLL |
|---|---|---|
| Download | [miva_4.x_nt_api_module.zip](./miva_4.x_nt_api_module.zip) | [miva_4.x_nt_commerce_lib_api_module.zip](./miva_4.x_nt_commerce_lib_api_module.zip) |
| Source | [src/nt_20080313/](./src/nt_20080313/) | [src/nt_commerce_lib/](./src/nt_commerce_lib/) |
| Files | `plugnpay.mv`, `plugnpay.mvc`, release notes | `plugnpay.mv`, `plugnpay.mvc`, `pnpmiva.dll`, `readmemivant.txt` |
| Extra methods | MocaPay, Gift Card | Credit cards + ACH |
| Checkout | Onsite → `pnpremote.cgi` | Onsite → `pnpremote.cgi` |
| Card data on your server | Yes | Yes |
| Status | **Current** for Merchant 4.x in this repo | Legacy Windows helper when Mia/Empresa needs a DLL |

## Remote API (2008-03-13) — preferred

- Source: [src/nt_20080313/](./src/nt_20080313/)
- Download: [miva_4.x_nt_api_module.zip](./miva_4.x_nt_api_module.zip)
- Quick install: [INSTALL.txt](./INSTALL.txt)
- Release notes: [src/nt_20080313/PlugNPay_ReleaseDoc.txt](./src/nt_20080313/PlugNPay_ReleaseDoc.txt) (also `.doc`)
- Module release doc version **1.1** (2008-01-24); package dated **2008-03-13**

Posts to Smart Screens-era Remote API endpoint `https://pay1.plugnpay.com/payment/pnpremote.cgi`. Extends the earlier v4 module with MocaPay and Gift Card fields.

### Requirements

- Miva Merchant **v4.x** (module API 4.14)
- Upload `.mv` if Merchant is below 4.14; upload `.mvc` if Merchant is 4.14 or newer
- Storefront HTTPS strongly recommended (PCI)

### Install steps

1. Download [miva_4.x_nt_api_module.zip](./miva_4.x_nt_api_module.zip) (or use `src/nt_20080313/`).
2. Admin → Modules → Add Module → upload `plugnpay.mvc` (or `plugnpay.mv` if required).
3. Store → Payment Configuration → enable **Plug & Pay Technologies Inc. v1.0**.
4. Configure publisher / gateway options on the PlugNPay tab.

## Remote API + commerce library DLL (legacy Windows)

- Source: [src/nt_commerce_lib/](./src/nt_commerce_lib/)
- Download: [miva_4.x_nt_commerce_lib_api_module.zip](./miva_4.x_nt_commerce_lib_api_module.zip)
- Quick install: [INSTALL_COMMERCE_LIB.txt](./INSTALL_COMMERCE_LIB.txt)
- Original NT notes: [src/nt_commerce_lib/readmemivant.txt](./src/nt_commerce_lib/readmemivant.txt)

Historically shipped as `miva_nt_pre4.0.zip` / `PnPMiva_NT.zip` (identical). Despite the `pre4.0` name, `plugnpay.mv` declares Merchant **v4.x** / API **4.14**. Register `pnpmiva.dll` as commerce method **PlugNPay** in Miva Mia or Empresa, then upload the module.

## Development layout

```
Miva_v4.x/
  README.md
  INSTALL.txt
  INSTALL_COMMERCE_LIB.txt
  miva_4.x_nt_api_module.zip
  miva_4.x_nt_commerce_lib_api_module.zip
  src/
    nt_20080313/       # 2008 package (+ release notes)
    nt_commerce_lib/   # DLL + readmemivant.txt
```
