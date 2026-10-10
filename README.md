# amneziawg-go for Windows

Unofficial Windows builds of [amneziawg-go](https://github.com/amnezia-vpn/amneziawg-go), the
userspace AmneziaWG implementation. Upstream publishes no Windows binaries, so this repository
builds them.

- **Source:** the official upstream tags, unmodified. Nothing here but the build workflow.
- **Build:** [GitHub Actions](.github/workflows/build.yml), every day: when upstream has a new tag,
  it is built for Windows x64, arm64 and x86 (`CGO_ENABLED=0 go build -trimpath -ldflags '-s -w'`)
  and published as a release with the same tag.
- **Checking a download:** `SHA256SUMS` in every release, and the SHA-256 digest GitHub shows for
  each asset. The release notes name the upstream commit the build comes from.
- **Running:** `amneziawg-go-windows-amd64.exe <interface name>` as SYSTEM (the control pipe is
  owned by SYSTEM), with `wintun.dll` next to it; set it up with `awg setconf` from
  [amneziawg-tools](https://github.com/amnezia-vpn/amneziawg-tools/releases). Upstream calls the
  Windows build a test program; for a full Windows client see [amnezia.org](https://amnezia.org).

Used by AppVpn (a private Xray / sing-box / AmneziaWG client for Windows) to update its AmneziaWG core.

## License

amneziawg-go is MIT licensed (Copyright © WireGuard LLC and the Amnezia authors); its `LICENSE`
ships with every release. The workflow in this repository is MIT licensed as well.
