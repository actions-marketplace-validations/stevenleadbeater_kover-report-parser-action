# GitHub Action for parsing coverage test reports for kotlin projects using Kover

Run coverage tests, parse the results for use in CI / CD

## Usage
```yaml
name: Test coverage

on:
  push:
    branches:
      - 'main'
    tags-ignore:
      - '**'

jobs:

  collect_coverage:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/setup-java@v1
        with:
          java-version: 11
      - name: Grant execute permission for gradlew
        shell: bash
        run: chmod +x gradlew
      - name: Get coverage
        shell: bash
        run: ./gradlew koverReport
      - name: Parse coverage
        id: parse_coverage
        uses: stevenleadbeater/kover-report-parser-action@0.0.1
```

## Outputs

### `line_covered`:
Lines covered from report file

### `line_missed`:
Lines missed from report file

### `instruction_covered`:
Instructions covered from report file

### `instruction_missed`:
Instructions missed from report file

### `branch_covered`:
Branches covered from report file

### `branch_missed`:
Branches missed from report file

### `method_covered`:
Methods covered from report file

### `method_missed`:
Methods missed from report file

### `class_covered`:
Classes covered from report file

### `class_missed`:
Classes missed from report file

## License

The action and documentation in this project are released under the [MIT License](LICENSE-MIT.txt).

