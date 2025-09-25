# Contributing

This project uses submodules so that actions may be added to the GitHub marketplace. Clone with:

```bash
git clone --recurse-submodules https://github.com/wasmCloud/actions.git
```

## Lint

We use [GitHub Super-Linter](https://github.com/github/super-linter) to ensure code quality and consistency. You can run the linter locally using Docker:

```bash
# optionally add --platform linux/amd64 if on arm
docker run \
   --platform linux/amd64 \
   -e "FILTER_REGEX_EXCLUDE=dist/**/*" \
   -e VALIDATE_JAVASCRIPT_ES=false \
   -e VALIDATE_JSCPD=false \
   -e VALIDATE_TYPESCRIPT_ES=false \
   -e VALIDATE_BIOME_FORMAT=false \
   -e VALIDATE_BIOME_LINT=false \
   -e FIX_MARKDOWN_PRETTIER=true \
   -e FIX_YAML_PRETTIER=true \
   -e FIX_GITHUB_ACTIONS_ZIZMOR=true \
   -e DEFAULT_BRANCH=main \
   -e RUN_LOCAL=true \
   -v .:/tmp/lint \
   ghcr.io/super-linter/super-linter:slim-latest
```
