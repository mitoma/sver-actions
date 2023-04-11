# Setup action

This action downloads and installs [sver][].

## Usage

Install sver and set the path just by adding the following line to steps.

```yaml
- uses: mitoma/sver-actions/setup@v1
```

With all options set:

```yaml
- uses: mitoma/sver-actions/exec@v1
  with:
    os: linux
    version: v0.1.14
    sha256sum: 407875b9e2263fb3ca94a6be166cd280f92404f01b1a00989a6deec441635706
```

### option

| name      | value                                    |
| --------- | ---------------------------------------- |
| os        | `linux` or `macos` or `windows`          |
| version   | released sver version. [sver releases][] |
| sha256sum | sha256sum of artifact zip file           |

[sver]: https://github.com/mitoma/sver
[sver releases]: https://github.com/mitoma/sver/releases
