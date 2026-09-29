# npm Publish Action

A composite GitHub Action that sets up Node.js, installs dependencies with the selected package manager (npm / pnpm / bun), and publishes the package to npm via `npm publish`. Just check out your repository and reference it with `uses` in your workflow.

> example `.github/workflows/release.yml`

```yaml
name: Release

on:
  push:
    tags:
      - 'v*'

jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v7
      
      - uses: lonewolfyx-workflows/npm-public-actions@main
        with:
          package-manager: pnpm
        permissions:
          contents: write
          id-token: write
      
      - run: npx genereleaselog@latest
        env:
          GITHUB_TOKEN: ${{secrets.GITHUB_TOKEN}}
```
