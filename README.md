# Shopping Cart - Miva Merchant Payment Modules

Easy to install payment modules for Miva Merchant.
These packages post card-not-present authorizations to PlugnPay Remote API (`pnpremote.cgi`). Card data is collected on the merchant storefront.

Source headers and `Module_API_Version` values show **two** Miva Merchant lines — not a single v2.x set:

| Folder | Declared in `plugnpay.mv` | `Module_API_Version` | `Module_Version` |
|---|---|---|---|
| [Miva_v2.x](./Miva_v2.x/) | `Miva Merchant v2.x` | `2.1` | `2.11` |
| [Miva_v4.x](./Miva_v4.x/) | `Miva Merchant v4.x` | `4.14` | `4.2400` |

## Downloads by Miva Merchant version

### Miva Merchant v4.x (current in this repo — Windows NT)

* **Remote API (2008-03-13)** — preferred v4 package; adds MocaPay / Gift Card support
  - [Download](./Miva_v4.x/miva_4.x_nt_api_module.zip)
  - Source: [./Miva_v4.x/src/nt_20080313/](./Miva_v4.x/src/nt_20080313/)
  - Docs: [package README](./Miva_v4.x/README.md) · [INSTALL.txt](./Miva_v4.x/INSTALL.txt)
* **Remote API + commerce library DLL** — older Windows package with `pnpmiva.dll` for Miva Mia / Empresa
  - [Download](./Miva_v4.x/miva_4.x_nt_commerce_lib_api_module.zip)
  - Source: [./Miva_v4.x/src/nt_commerce_lib/](./Miva_v4.x/src/nt_commerce_lib/)
  - Docs: [package README](./Miva_v4.x/README.md) · [INSTALL_COMMERCE_LIB.txt](./Miva_v4.x/INSTALL_COMMERCE_LIB.txt)

Package overview: [./Miva_v4.x/README.md](./Miva_v4.x/README.md)

### Miva Merchant v2.x (legacy — Unix commerce libraries)

* **Remote API — Linux** — `plugnpay.mv` + `pnpmiva.so`
  - [Download](./Miva_v2.x/miva_2.x_linux_api_module.tar.gz)
  - Source: [./Miva_v2.x/src/Linux/](./Miva_v2.x/src/Linux/)
* **Remote API — FreeBSD** — `plugnpay.mv` + `pnpmiva.so`
  - [Download](./Miva_v2.x/miva_2.x_freebsd_api_module.tar.gz)
  - Source: [./Miva_v2.x/src/FreeBSD/](./Miva_v2.x/src/FreeBSD/)
* **Remote API — Solaris (SPARC)** — `plugnpay.mv` + `pnpmiva.so`
  - [Download](./Miva_v2.x/miva_2.x_solaris_api_module.tar.gz)
  - Source: [./Miva_v2.x/src/solaris/](./Miva_v2.x/src/solaris/)

Docs: [package README](./Miva_v2.x/README.md) · [INSTALL.txt](./Miva_v2.x/INSTALL.txt)

## Installation

For complete instructions, open the README inside the package folder (or the linked docs above).

### Miva Merchant 4.x (Windows)

1. Download [miva_4.x_nt_api_module.zip](./Miva_v4.x/miva_4.x_nt_api_module.zip) (preferred) or the commerce-lib package if you need `pnpmiva.dll`.
2. For Merchant **below 4.14**, upload `plugnpay.mv`. For **4.14 and above**, upload compiled `plugnpay.mvc`.
3. Enable **Plug & Pay Technologies Inc. v1.0** under Store → Payment Configuration.
4. If using the commerce-lib package, register `pnpmiva.dll` as commerce method **PlugNPay** in Miva Mia / Empresa first.

- Quick install: [Miva_v4.x/INSTALL.txt](./Miva_v4.x/INSTALL.txt)
- Commerce library: [Miva_v4.x/INSTALL_COMMERCE_LIB.txt](./Miva_v4.x/INSTALL_COMMERCE_LIB.txt)

### Miva Merchant 2.x (Unix)

1. Download the archive for your OS (Linux, FreeBSD, or Solaris).
2. Install `pnpmiva.so` as a Miva commerce library and name the method **PlugNPay**.
3. Upload `plugnpay.mv` as a payment module in Miva admin.
4. Enable it under the store’s Payment Configuration.

- Quick install: [Miva_v2.x/INSTALL.txt](./Miva_v2.x/INSTALL.txt)

## Usage

### Remote API

* Checkout collects payment data on the Miva Merchant storefront (increases PCI scope).
* The module posts to `https://pay1.plugnpay.com/payment/pnpremote.cgi`.
* Charge method can be online (automatic capture) or offline (authorize only, capture later in PlugnPay Merchant Admin).
* v2.x Unix builds use a platform `pnpmiva.so` commerce library (`client=miva`).
* v4.x Windows commerce-lib build uses `pnpmiva.dll` (`client=pnpmiva`).
* v4.x 2008 package adds MocaPay and Gift Card payment methods; see release notes in that package.

## Repository layout

```
shopping-cart-Miva/
  README.md
  Miva_v4.x/                      # current (Merchant v4.x / API 4.14) — Windows Remote API
    README.md
    INSTALL.txt
    INSTALL_COMMERCE_LIB.txt
    miva_4.x_nt_api_module.zip
    miva_4.x_nt_commerce_lib_api_module.zip
    src/nt_20080313/
    src/nt_commerce_lib/
  Miva_v2.x/                      # legacy (Merchant v2.x / API 2.1) — Unix Remote API
    README.md
    INSTALL.txt
    miva_2.x_linux_api_module.tar.gz
    miva_2.x_freebsd_api_module.tar.gz
    miva_2.x_solaris_api_module.tar.gz
    src/Linux/
    src/FreeBSD/
    src/solaris/
```

Historical note: `Windows/PnPMiva_NT.zip` was byte-identical to `miva_nt_pre4.0.zip` and is represented here once as `miva_4.x_nt_commerce_lib_api_module.zip`. Despite the old `pre4.0` filename, that package’s `plugnpay.mv` declares **Miva Merchant v4.x** / API **4.14**.

## Support

Provided AS IS. See [PlugnPay docs](https://docs.plugnpay.com/) and the module README for integration details.
