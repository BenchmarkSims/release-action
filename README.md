# Release Action

This action will help Gitea users to publish release and attachments.

## Example

```yaml
name: release

on: 
  push:
    tags:
      - '*'

jobs:
  release:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3
        with:
          fetch-depth: 0

      - name: setup go
        uses: actions/setup-go@v4
        with:
          go-version: '>=1.20.1'

      - name: go build
        run: go build -o bin/myapp

      - name: Use Go Action  
        id: use-go-action
        uses: https://github.com/BenchmarkSims/release-action.git@main
        with:
          files: |-
            bin/**
          api_key: '${{secrets.RELEASE_TOKEN}}'
```
