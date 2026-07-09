# github-workflows

Reusable GitHub Actions workflows for Rust projects.

## Available Workflows

### CI Workflow

A reusable CI workflow that runs formatting, check, clippy, and test checks.

**Inputs:**

| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `apt_packages` | string | `""` | Additional apt packages to install on Ubuntu |
| `check_args` | string | `""` | Additional arguments for `cargo check` |
| `clippy_args` | string | `""` | Additional arguments for `cargo clippy` |
| `test_args` | string | `""` | Additional arguments for `cargo test` |

**Usage:**

```yaml
jobs:
  ci:
    uses: riccione/github-workflows/.github/workflows/rust-ci.yml@main
    with:
      apt_packages: "libssl-dev pkg-config"
```

### Release Workflow

A reusable release workflow that builds binaries for Linux, Windows, and macOS, generates a changelog, and uploads artifacts to GitHub Releases.

**Inputs:**

| Input | Type | Default | Required | Description |
|-------|------|---------|----------|-------------|
| `apt_packages` | string | `""` | No | Additional apt packages to install on Ubuntu |
| `bin_name` | string | - | Yes | Name of the compiled binary |
| `use_upx` | boolean | `true` | No | Compress binaries with UPX |
| `cargo_args` | string | `"--locked"` | No | Additional cargo arguments |
| `tag` | string | - | Yes | Release tag to upload artifacts to |

**Usage:**

```yaml
jobs:
  release:
    uses: riccione/github-workflows/.github/workflows/rust-release.yml@main
    with:
      bin_name: my-app
      tag: ${{ github.ref_name }}
```

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/my-feature`)
3. Commit your changes (`git commit -m 'feat: add new feature'`)
4. Push to the branch (`git push origin feature/my-feature`)
5. Open a Pull Request

Please follow [Conventional Commits](https://www.conventionalcommits.org/) for commit messages.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

Copyright (c) 2026 riccione
