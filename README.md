# action-setup

A GitHub Action to set up Toit and optionally the Toit QEMU fork.

## Basic usage

See [action.yml](action.yml) for a complete list of options and outputs.

```yaml
steps:
- uses: actions/checkout@v4

- uses: toitlang/action-setup@v1
  with:
    toit-version: 'v2.0.0-alpha.189'

- run: toit.run main.toit
```

If no `toit-version` is specified, the latest version is used.

## QEMU

The action can optionally install the Toit QEMU fork:

```yaml
- uses: toitlang/action-setup@v1
  with:
    toit-version: 'v2.0.0-alpha.195'
    qemu-version: 'v9.2.2-toitlang.1'
```

If `qemu-version` is omitted, QEMU is not installed. Set it to `latest` to
install the latest published Toit QEMU release:

```yaml
- uses: toitlang/action-setup@v1
  with:
    qemu-version: latest
```

The action selects the archive matching the runner operating system and
architecture, verifies it against the release's `SHA256SUMS`, and adds its
`bin` directory to `PATH`. It also sets `QEMU_SYSTEM_XTENSA` and
`QEMU_SYSTEM_RISCV32` for subsequent steps.

For reproducible CI, prefer an exact `qemu-version` over `latest`.
