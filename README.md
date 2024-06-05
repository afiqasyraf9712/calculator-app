name: Super-Linter

on:
  pull_request:
    branches:
      - temp-jenkins2

jobs:
  super-lint:
    name: Lint README.md in Pull Request
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Run Super-Linter for README.md
        uses: github/super-linter@v4
        with:
          files: README.md
        env:
          DEFAULT_BRANCH: temp-jenkins2
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
