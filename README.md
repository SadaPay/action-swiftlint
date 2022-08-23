# GitHub Action for SwiftLint

This Action executes [SwiftLint](https://github.com/realm/SwiftLint) and generates annotations from SwiftLint Violations.

## Usage

An example workflow(`.github/workflows/swiftlint.yml`) to executing SwiftLint follows:

```yaml
name: SwiftLint

on:
  pull_request:
    paths:
      - '.github/workflows/swiftlint.yml'
      - '.swiftlint.yml'
      - '**/*.swift'

jobs:
  SwiftLint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1
      - name: GitHub Action for SwiftLint
        uses: SadaPay/ios-swiftlint-action@1.0.0
      - name: GitHub Action for SwiftLint with --strict
        uses: SadaPay/ios-swiftlint-action@1.0.0
        with:
          args: --strict
      - name: GitHub Action for SwiftLint (Only files changed in the PR)
        uses: SadaPay/ios-swiftlint-action@1.0.0
        env:
          DIFF_BASE: ${{ github.base_ref }}
      - name: GitHub Action for SwiftLint (Different working directory)
        uses: SadaPay/ios-swiftlint-action@1.0.0
        env:
          WORKING_DIRECTORY: Source
```
