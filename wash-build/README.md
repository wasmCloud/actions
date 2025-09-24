# wash-build

Build WebAssembly components using wash CLI and output the component path.

## Features

- A common action for getting the component_path after a build
- Validates that the component_path exists after the build
- JSON output parsing with `jq` for robust component path extraction
- Error handling and validation of build output

## Usage

Add the following step to your GitHub workflow:

```yaml
- name: Build component
  id: build
  uses: wasmcloud/actions/wash-build@main

- name: Use the built component
  run: echo "Component built at: ${{ steps.build.outputs.artifact_path }}"
```

## Prerequisites

You must have the `wash` CLI and `jq` installed and available in your PATH. We recommend using the
[wasmcloud/setup-wash-action](../setup-wash-action) prior to this action to install wash.

## Outputs

- `component_path`: Path to the built WebAssembly component
