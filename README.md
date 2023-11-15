# action-setup

A GitHub Action to setup Toit.

## Basic usage

See [action.yml](action.yml) for a complete list of options and outputs.

```yaml
steps:
- uses: actions/checkout@v4

- uses: toitware/action-setup@v1
  with:
    toit-version: '2.0.0-alpha.120'

- run: toit.run main.toit
```

If no `toit-version` is specified, the latest version is used.
