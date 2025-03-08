
PolicyKit (PolKit) is an authorization service on Linux that allowed software to communicate with each other.

PolKit works with two file groups:
- actions/policies (`/usr/share/polkit-1/actions`)
- rules (`/usr/share/polkit-1/rules.d`)

Custom rules can also be set in `.pkla` files

Also comes with three additional programs:
- `pkexec` (same as sudo, can also run as root)
- `pkaction`
- `pkcheck`

### Vulnerabilities

- [CVE-2021-4034](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-4034) PwnKit
- 