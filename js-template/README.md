# JS Semantic Release Template

A ready-to-use template for JavaScript/Node.js projects configured with [`semantic-release`](https://github.com/semantic-release/semantic-release).

## Features

This template sets up automated version management and package publishing with the following enhancements:

- **Conventional Commits with PR Support**: Uses the `conventionalcommits` preset with a custom parser pattern that correctly handles GitHub/Bitbucket "Merged PR" and merge commit message prefixes.
- **Detailed Release Rules**: Configured to trigger patch releases for `perf`, `refactor`, and `style` changes in addition to standard `fix` and `feat` (minor) releases.
- **Standard Plugins**:
  - **`@semantic-release/commit-analyzer`**: Determines the next release version.
  - **`@semantic-release/release-notes-generator`**: Generates release notes.
  - **`@semantic-release/changelog`**: Updates `CHANGELOG.md`.
  - **`@semantic-release/npm`**: Updates version in `package.json` (configured with `npmPublish: false` by default).
  - **`@semantic-release/git`**: Commits release assets back to the repository.
  - **`@semantic-release/github`**: Creates GitHub releases.

## Getting Started

1. Copy `.releaserc.json` and `package.json` details into your project.
2. Install the necessary development dependencies:

   ```bash
   npm install -D semantic-release @semantic-release/commit-analyzer @semantic-release/release-notes-generator @semantic-release/changelog @semantic-release/npm @semantic-release/git @semantic-release/github conventional-changelog-conventionalcommits
   ```

3. Setup CI/CD pipeline (e.g., GitHub Actions) to run `npx semantic-release` on your main branch.
4. Ensure your `GITHUB_TOKEN` (and `NPM_TOKEN` if you decide to publish to an npm registry) are configured in your CI environment.
