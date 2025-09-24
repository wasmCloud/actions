# setup-wash-cargo-auditable

Configures cargo-auditable for wash builds with SBOM generation.

## Features

- Installs `cargo-auditable` and `cargo-audit` tools
- Creates/updates `.wash/config.json` with custom build command.
  I considered alias'ing `cargo` to `cargo auditable` but that might
  cause unintended downstream effects, but could also be fine. I opted for this approach instead as it is a handy way to always get a wash build that is in release mode and ready to publish.
- Preserves existing configuration by merging in with custom build command.

## Usage

Add the following step to your GitHub workflow before any wash build steps:

```yaml
- name: Setup wash cargo-auditable
  uses: wasmcloud/actions/setup-wash-cargo-auditable@main
```

Do this before running `wash build` as this action sets up a custom build command in `.wash/config.json`.
You must also have the `wash` CLI installed and available in your PATH. We recommend using the
[wasmcloud/setup-wash-action](../setup-wash-action) prior to this action to install wash.
