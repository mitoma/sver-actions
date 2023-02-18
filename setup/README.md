# Setup action

This action downloads and installs [sver][].

## Usage

Install sver and set the path just by adding the following line to steps.

```yaml
- uses: mitoma/sver-actions/setup@v1
```

With all options set:

```yaml
- uses: ./.github/actions/setup_sver
  with:
    os: linux
    version: v0.1.14
```

### option

| name    | value                                    |
| ------- | ---------------------------------------- |
| os      | `linux` or `macos` or `windows`          |
| version | released sver version. [sver releases][] |

[sver]: https://github.com/mitoma/sver
[sver releases]: https://github.com/mitoma/sver/releases
