# fakegreen GitHub Action (standalone repo)

This composite GitHub Action runs [fakegreen](https://github.com/fitzyracing1/fakegreen) on a pull request diff and annotates every finding. It needs no LLM and no API key. The repo contains only `action.yml`, the README and the LICENSE.

## Usage

```yaml
on: pull_request
jobs:
  fakegreen:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0
      - uses: fitzyracing1/fakegreen-action@v1
```

| Input | Default | Description |
|---|---|---|
| `version` | `latest` | fakegreen version from npm |
| `base` | PR base branch | base ref to diff against |
| `fail-on` | `high` | `high`, `medium`, `low`, `none` |
| `args` | | extra fakegreen arguments |

A failing check from this action means the CI run is **dark**. A clean diff keeps it **lit**. The fakegreen repo also ships its own `action.yml`. For rules and configuration, see the [fakegreen docs](https://github.com/fitzyracing1/fakegreen/tree/main/docs).

MIT License. Copyright (c) 2026 Joshua Almeida
