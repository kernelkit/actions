# kernelkit/actions

Reusable GitHub Actions for KernelKit projects.

## Actions

### `cache-restore`

Restores `dl/` and `.ccache/` build caches for [Buildroot][]-based projects.

> **Note:** Cache keys hash `.git/modules/buildroot/HEAD`, `configs/*`, and
> `package/*/*.hash`, so this action assumes a Buildroot project layout with
> a `buildroot` submodule.

**Usage:**

```yaml
- uses: kernelkit/actions/cache-restore@v1
  with:
    target: ${{ env.TARGET }}
```

**Inputs:**

| Input           | Required | Default    | Description                                     |
|-----------------|----------|------------|-------------------------------------------------|
| `target`        | yes      |            | Build target, used in the `.ccache/` cache key  |
| `dl-prefix`     | no       | `dl`       | Prefix for the `dl/` cache key                  |
| `ccache-prefix` | no       | `ccache`   | Prefix for the `.ccache/` cache key             |
| `enabled`       | no       | `true`     | Set to `false` to skip cache restoration        |

---

### `podman-cleanup`

Cleans up stale Podman state (containers, volumes, images) left over from
previous CI runs on self-hosted runners.

**Usage:**

```yaml
- uses: kernelkit/actions/podman-cleanup@v1
```

No inputs.

---

## License

MIT — see [LICENSE](LICENSE).

[Buildroot]: https://buildroot.org
