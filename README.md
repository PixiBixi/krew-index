# PixiBixi krew index

A [krew](https://krew.sigs.k8s.io/) custom index hosting kubectl plugins
maintained by PixiBixi. Plugin manifests live under `plugins/` and are pushed
automatically by each plugin's GoReleaser pipeline on release.

## Usage

```bash
kubectl krew index add pixibixi https://github.com/PixiBixi/krew-index.git
kubectl krew install pixibixi/ice
kubectl krew install pixibixi/klens
```

Update later:

```bash
kubectl krew update
kubectl krew upgrade ice klens
```

> Plugins in this index are not audited by the Krew maintainers. Install at your own risk.

## Plugins

| Plugin | Source | Description |
|--------|--------|-------------|
| `ice` | [kubectl-ice](https://github.com/PixiBixi/kubectl-ice) | Container-level config & metrics inside Pods (maintained fork) |
| `klens` | [kubectl-klens](https://github.com/PixiBixi/kubectl-klens) | Quick read-only cluster inspection shortcuts |

## How manifests get here

Each plugin repo's `.goreleaser.yml` has a `krews:` publisher pointing its
`repository` at this repo. On a tagged release it commits the rendered
`plugins/<name>.yaml` here, using a fine-grained PAT (`KREW_INDEX_TOKEN`)
with `contents:write` scoped to this repo only.
