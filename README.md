# issue-management

[![Continuous integration](https://github.com/stairwaytowonderland/issue-management/actions/workflows/ci.yaml/badge.svg)](https://github.com/stairwaytowonderland/issue-management/actions/workflows/ci.yaml)
[![GitHub latest release](https://img.shields.io/github/v/release/stairwaytowonderland/issue-management?include_prereleases&logo=rocket)](https://github.com/stairwaytowonderland/stairwaytowonderland/issue-management/releases)
[![GitHub last commit](https://img.shields.io/github/last-commit/stairwaytowonderland/issue-management?logo=git)](https://github.com/stairwaytowonderland/stairwaytowonderland/issue-management/commits/main)
[![GitHub license](https://img.shields.io/github/license/stairwaytowonderland/issue-management?logo=opensourceinitiative&labelCol&color=yellow&logoColor=white)](https://github.com/stairwaytowonderland/stairwaytowonderland/issue-management/tree/main/LICENSE)
[![semantic-release: conventionalcommits](https://img.shields.io/badge/semantic--release-cc-FE5196?logo=semantic-release)](https://github.com/semantic-release/semantic-release)
[![pre-commit](https://img.shields.io/badge/pre--commit-FAB040?logo=pre-commit&logoColor=black)](https://github.com/pre-commit/pre-commit)

A centralized issue management repository. :lady_beetle:

## :cactus: Project structure

> [!NOTE]
>
> `tree -a -F -L 3 -I '.git|.vscode' --gitignore --dirsfirst .`

```none
./
├── .github/
│   ├── workflows/
│   │   ├── ci.yaml
│   │   ├── conventional-commit.yaml
│   │   ├── create-labels.yaml
│   │   ├── import-csv-issues.yaml
│   │   ├── pre-commit.yaml
│   │   ├── publish.yaml
│   │   ├── release.yaml
│   │   └── repository-created.yaml
│   └── dependabot.yml
├── .editorconfig
├── .gitignore
├── .markdownlint.json
├── .pre-commit-config.yaml
├── .prettierignore
├── .prettierrc
├── .releaserc
├── LICENSE
├── README.md
├── TODO.csv
└── TODO.example.csv
```

---

## :arrows_counterclockwise: Reusable Workflows

### `import-csv-issues`

**Description:**
Reusable workflow to import issues from a CSV file.

**Usage Example:**

```yaml
uses: stairwaytowonderland/actions/.github/workflows/import-csv-issues.yaml@main
with:
  csv-path: path/to/issues.csv
  dry-run: false
  batch: true
  allow-duplicates: false
  allow-closed-duplicates: false
  ref: main
  action-ref: main
  node-version: 24
  max-parallel: 5
secrets: inherit
```

**Inputs:**

| Name                      | Description                                                                     | Required | Type    | Default    |
| ------------------------- | ------------------------------------------------------------------------------- | -------- | ------- | ---------- |
| `ref`                     | Git ref of the shared actions repo to use (e.g. `main` or a tag/commit)         | No       | string  | `main`     |
| `action-ref`              | Git ref of the shared actions repo to use (e.g. `main` or a tag/commit)         | No       | string  | `main`     |
| `node-version`            | Node.js version to use for parsing CSV (e.g. `18`, `20`, `24`)                  | No       | string  | `24`       |
| `dry-run`                 | Dry run (no issues created)                                                     | No       | boolean | `true`     |
| `max-parallel`            | Maximum number of parallel issue creations (only applies when `batch` is false) | No       | number  | `5`        |
| `batch`                   | Create issues in batches (by type)                                              | No       | boolean | `true`     |
| `allow-duplicates`        | Allow creating duplicate issues                                                 | No       | boolean | `false`    |
| `allow-closed-duplicates` | Allow creating duplicate issues for closed issues                               | No       | boolean | `false`    |
| `csv-path`                | Path (relative) to the CSV file                                                 | Yes      | string  | `TODO.csv` |

**Secrets:**

| Name           | Description                                                                     |
| -------------- | ------------------------------------------------------------------------------- |
| `github-token` | Optional token with permissions to create issues (falls back to `GITHUB_TOKEN`) |

---

## :sparkles: Contributing

### :robot: Commit Message Guidelines

- Write clear, concise commit messages that follow the
  [![conventional-commit](https://img.shields.io/badge/conventional--commit-FE5196?logo=conventionalcommits&logoColor=white)](https://www.conventionalcommits.org/)&nbsp;standard.
- The allowed _prefixes_ for this project are the following:

    ```json
    [
      "build",
      "chore",
      "ci",
      "docs",
      "feat",
      "fix",
      "perf",
      "refactor",
      "revert",
      "style",
      "test"
    ]
    ```

> [!NOTE]
>
> See [Contributing Guidelines](https://github.com/stairwaytowonderland/issue-management?tab=contributing-ov-file#contributing-guidelines)
> for more information.
