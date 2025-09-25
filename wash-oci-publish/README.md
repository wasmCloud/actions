# wash-oci-publish

Publish WebAssembly components to OCI registries with optional attestation support.

## Features

- Configurable registry input (defaults to `ghcr.io`)
- Automatic registry login using GitHub credentials
- Component publishing with digest capture
- Artifact attestation support for supply chain security
- GitHub release upload integration
- Repository name normalization (lowercase)

## Usage

Add the following step to your GitHub workflow:

```yaml
- name: Publish component
  uses: wasmcloud/actions/wash-oci-publish@main
  with:
    component_path: ${{ steps.build.outputs.artifact_path }}
    registry: ghcr.io # optional, defaults to ghcr.io
    attestation: true # optional, defaults to false
```

## Prerequisites

You must have the `wash` CLI installed and available in your PATH. We recommend using the
[wasmcloud/setup-wash-action](../setup-wash-action) prior to this action to install wash.

## Required Permissions

Workflows using this action will need the following permissions:

```yaml
permissions:
  contents: write
  packages: write
  attestations: write
  id-token: write
```

## Inputs

- `registry`: Container registry to push to (optional, defaults to `ghcr.io`)
- `component_path`: Path to the built WebAssembly component (required)
- `attestation`: Whether to generate an attestation for the published artifact (optional, defaults to `false`)
