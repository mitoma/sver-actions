# Setup action

This action downloads and installs [sver][].

## Usage

Install sver and set the path just by adding the following line to steps.

```yaml
- uses: mitoma/sver-actions/setup@v1
```

If you do not set `os` and `arch`, the action uses the operating system and
CPU architecture of the runner it runs on, so it works on Linux, macOS and
Windows runners, including ARM64, without any options.

With all options set:

```yaml
- uses: mitoma/sver-actions/setup@v1
  with:
    os: linux
    arch: amd64
    version: v0.1.14
    sha256sum: 407875b9e2263fb3ca94a6be166cd280f92404f01b1a00989a6deec441635706
```

### option

| name      | value                                                                       |
| --------- | --------------------------------------------------------------------------- |
| os        | `linux` or `macos` or `windows` (defaults to the runner's operating system) |
| arch      | `amd64` or `arm64` (defaults to the runner's CPU architecture)              |
| version   | released sver version. [sver releases][]                                    |
| sha256sum | SHA-256 hash of the artifact zip file                                       |

Please refer to the `SHASUMS256.txt` included in the [sver releases][] for the sha256 hash.

[sver]: https://github.com/mitoma/sver
[sver releases]: https://github.com/mitoma/sver/releases
