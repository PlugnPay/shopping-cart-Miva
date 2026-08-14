# Miva Merchant v2.x — PlugnPay Payment Module

Legacy packages for **Miva Merchant v2.x**. Source `plugnpay.mv` declares:

- Header: `Miva Merchant v2.x`
- `Module_API_Version`: **2.1**
- `Module_Version`: **2.11**
- CVS id dated **2000-03-19**

Each OS archive ships the same `plugnpay.mv` plus a platform-specific `pnpmiva.so` commerce library. Prefer [Miva_v4.x](../Miva_v4.x/) when running Merchant 4.x.

## Choose a package

| | Linux | FreeBSD | Solaris |
|---|---|---|---|
| Download | [miva_2.x_linux_api_module.tar.gz](./miva_2.x_linux_api_module.tar.gz) | [miva_2.x_freebsd_api_module.tar.gz](./miva_2.x_freebsd_api_module.tar.gz) | [miva_2.x_solaris_api_module.tar.gz](./miva_2.x_solaris_api_module.tar.gz) |
| Source | [src/Linux/](./src/Linux/) | [src/FreeBSD/](./src/FreeBSD/) | [src/solaris/](./src/solaris/) |
| Binary | `pnpmiva.so` (ELF i386) | `pnpmiva.so` (ELF i386, FreeBSD 4.1.1) | `pnpmiva.so` (ELF SPARC32PLUS) |
| Checkout | Onsite → `pnpremote.cgi` | same | same |
| Card data on your server | Yes | Yes | Yes |
| Status | Legacy for Merchant 2.x | Legacy for Merchant 2.x | Legacy for Merchant 2.x |

## Remote API (Unix commerce library)

- Gateway URL in module: `https://pay1.plugnpay.com/payment/pnpremote.cgi`
- Commerce library identifies as `client=miva`
- Register the `.so` as commerce method **PlugNPay**, then upload `plugnpay.mv` in Miva admin
- Quick install: [INSTALL.txt](./INSTALL.txt)

### Requirements

- Miva Merchant **v2.x** (module API 2.1)
- Matching OS binary (Linux / FreeBSD / Solaris SPARC)
- Ability to register a Miva commerce library and upload a payment module
- Storefront HTTPS strongly recommended (PCI)

### Install steps

1. Download the archive for your OS (or use `src/`).
2. Install `pnpmiva.so` into the Miva commerce-library path / configuration; method name **PlugNPay** (case-sensitive).
3. In Miva admin → Modules → Add Module, upload `plugnpay.mv`.
4. Store → Payment Configuration → enable **Plug & Pay Technologies Inc. v1.0** and configure credentials.

## Development layout

```
Miva_v2.x/
  README.md
  INSTALL.txt
  miva_2.x_linux_api_module.tar.gz
  miva_2.x_freebsd_api_module.tar.gz
  miva_2.x_solaris_api_module.tar.gz
  src/
    Linux/      # plugnpay.mv + pnpmiva.so
    FreeBSD/    # plugnpay.mv + pnpmiva.so
    solaris/    # plugnpay.mv + pnpmiva.so
```
