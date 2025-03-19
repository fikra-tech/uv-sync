# uv-sync

> [!WARNING]
> This action is still semi-experimental.
> I’m happy to [hear feedback](https://github.com/ouhammmourachid/uv-sync/issues), though!

## Description

The `ouhammmourachid/uv-sync` GitHub Action allows you to easily install and manage dependencies using the `uv` package manager. This action supports setting up specific Python and `uv` versions, and provides flexibility to pass additional arguments to the `uv sync` command. It is designed to work across multiple operating systems and Python versions, making it a versatile tool for CI/CD workflows.

## Variables

- `python-version`: The version of Python to be used. Default is `3.x`.
- `uv-version`: The version of the `uv` package manager to be installed. Default is the latest version.
- `additional-args`: Additional arguments to be passed to the `uv sync` command. Default is an empty string.

## Usage

To use the `ouhammmourachid/uv-sync` GitHub Action in your workflow, add the following steps to your `.github/workflows/your-workflow.yml` file:

```yaml
name: CI

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout repository
      uses: actions/checkout@v2
    - name: Install uv-sync
      uses: ouhammmourachid/uv-sync@v1
      with:
        python-version: '3.11'
        uv-version: 'latest'
        additional-args: ''
        working-directory: '.'

    - name: Run a script
      run: uv run main.py
```