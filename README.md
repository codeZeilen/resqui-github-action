# resqui GitHub Action

A GitHub Action that runs [resqui](https://github.com/EVERSE-ResearchSoftware/QualityPipelines) to assess research software quality indicators and optionally upload results to DashVerse.

## Usage

```yaml
- name: Run resqui
  uses: EVERSE-ResearchSoftware/resqui-github-action@main
  with:
    github_token: ${{ secrets.GITHUB_TOKEN }}
```

## Inputs

| Input | Description | Required |
|-------|-------------|----------|
| `github_token` | GitHub token required for some indicator plugins | Yes |
| `config` | Path to the configuration file (e.g., `configurations/basic.json`) | No |
| `dashverse_token` | DashVerse token to upload the results | No |

## Examples

### Basic usage

```yaml
name: Run Resqui CI

on:
  push:

jobs:
  run-resqui:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Run resqui
        uses: EVERSE-ResearchSoftware/resqui-github-action@main
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
```

### With custom config and DashVerse upload

```yaml
name: Run Resqui CI

on:
  push:

jobs:
  run-resqui:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Run resqui
        uses: EVERSE-ResearchSoftware/resqui-github-action@main
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          config: configurations/basic.json
          dashverse_token: ${{ secrets.DASHVERSE_TOKEN }}
```
