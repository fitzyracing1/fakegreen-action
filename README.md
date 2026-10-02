# fakegreen GitHub Action

Catch AI coding agents faking a green build: skipped or deleted tests, weakened assertions, silenced linters, and neutered CI.

This Action runs [fakegreen](https://github.com/fitzyracing1/fakegreen) on your pull request diff and annotates every finding. No LLM, no API key.

## Usage

```yaml
name: fakegreen
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

## Inputs

| Input | Default | Description |
|---|---|---|
| `version` | `latest` | fakegreen version to run from npm |
| `base` | PR base branch | Base ref to diff against |
| `fail-on` | `high` | Minimum severity that fails the step (`high`, `medium`, `low`, `none`) |
| `args` | | Extra arguments passed to fakegreen |

See the [main fakegreen repo](https://github.com/fitzyracing1/fakegreen) for the full rule list and configuration.

## License

MIT
