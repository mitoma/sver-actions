# Exec action

This action run the command only when there is no previous successful job for the same version.

This action uses a tool called [sver][] to calculate the version.

## Usage

```yaml
- uses: mitoma/sver-actions/exec@v1
  with:
    phase: build
    github_token: ${{ secrets.GITHUB_TOKEN }}
    command: |
      cargo build
```

With all options set:

```yaml
# standard rust project example.
- uses: mitoma/sver-actions/exec@v1
  with:
    phase: build
    github_token: ${{ secrets.GITHUB_TOKEN }}
    path: .
    command: |
      cargo build --release
    # save cache only default branch
    cache_save_enable: ${{ github.ref == format('refs/heads/{0}', github.event.repository.default_branch) }}
    cache_key: cargo-${{ hashFiles('**/Cargo.lock') }}
    cache_restore-keys: |
      cargo-${{ hashFiles('**/Cargo.lock') }}
      cargo-
    cache_path: |
      ~/.cargo/registry
      ~/.cargo/git
      target
    artifact_name: build-result
    artifact_path: path/to/artifact
```

### Artifacts and caches

This action creates some artifacts and caches.

| type     | key format                  | description                                                  |
| -------- | --------------------------- | ------------------------------------------------------------ |
| artifact | `{phase}-{version}.success` | A zero-sized file to determine if this phase was successful. |
| artifact | `{artifact_name}-{version}` | An artifact produced in this phase.                          |
| cache    | `{cache_key}-{version}`     | Caches generated in this phase.                              |

### option

| name               | description                                                                                  |
| ------------------ | -------------------------------------------------------------------------------------------- |
| phase              | This option will upload a flag file to the artifact when building this version successfully. |
| github_token       | GitHub access token. You need permission to upload artifacts.                                |
| path               | The path on which sver is computed.                                                          |
| command            | Runs command-line programs using the bash.                                                   |
| cache_save_enable  | If true, save cache. If false, restore only. Default true.                                   |
| cache_key          | It has the same meaning as `key` in the [actions/cache][] parameter.                         |
| cache_restore-keys | It has the same meaning as `restore-keys` in the [actions/cache][] parameter.                |
| cache_path         | It has the same meaning as `path` in the [actions/cache][] parameter.                        |
| artifact_name      | It has the same meaning as `name` in the [actions/upload-artifact][] parameter.              |
| artifact_path      | It has the same meaning as `path` in the [actions/upload-artifact][] parameter.              |

[sver]: https://github.com/mitoma/sver
[actions/cache]: https://github.com/actions/cache#inputs
[actions/upload-artifact]: https://github.com/actions/upload-artifact
