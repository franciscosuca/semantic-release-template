# .NET Semantic Release Template

A ready-to-use template for .NET Core / C# projects configured with [`semantic-release`](https://github.com/semantic-release/semantic-release).

## Features

This template sets up automated version management and release automation with the following:

- **Conventional Commits with PR Support**: Uses the `conventionalcommits` preset with a custom parser pattern that correctly handles GitHub/Bitbucket "Merged PR" and merge commit message prefixes.
- **Semantic Versioning**: Configures release rules for major (breaking), minor (features), and patch (fixes/performance) releases.
- **Version File Management**:
  - Updates `VERSION.txt` with the new release version
  - Updates `.csproj` file version properties (`Version`, `AssemblyVersion`, `FileVersion`, `InformationalVersion`)
- **Standard Plugins**:
  - **`@semantic-release/commit-analyzer`**: Determines the next release version.
  - **`@semantic-release/release-notes-generator`**: Generates release notes with emoji-enhanced categories.
  - **`@semantic-release/changelog`**: Updates `CHANGELOG.md`.
  - **`@semantic-release/exec`**: Executes custom commands for version updates in `.csproj` files.
  - **`@semantic-release/git`**: Commits release assets back to the repository.

## Getting Started

1. **Copy Files**: Copy `.releaserc.json` and `package.json` to your project root.

2. **Update Placeholders**: Open `.releaserc.json` and replace:
   - `{{CSPROJ_PATH}}` with the path to your `.csproj` file (e.g., `MyProject/MyProject.csproj`)

3. **Install Dependencies**:

   ```bash
   npm install -D semantic-release @semantic-release/commit-analyzer @semantic-release/release-notes-generator @semantic-release/changelog @semantic-release/exec @semantic-release/git conventional-changelog-conventionalcommits
   ```

4. **Configure Your `.csproj`**: Ensure your `.csproj` file has these version properties (if they don't exist, add them):

   ```xml
   <Version>0.0.0</Version>
   <AssemblyVersion>0.0.0</AssemblyVersion>
   <FileVersion>0.0.0</FileVersion>
   <InformationalVersion>0.0.0</InformationalVersion>
   ```

5. **Setup CI/CD Pipeline** (e.g., GitHub Actions):

   ```yaml
   - name: Release
     run: npx semantic-release
     env:
       GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
   ```

6. **Commit and Push**: Use conventional commit messages to trigger releases:
   - `feat:` → minor version bump
   - `fix:` → patch version bump  
   - `BREAKING CHANGE:` → major version bump

## Customization

### Modifying Version Rules

Edit the `releaseRules` in `.releaserc.json` to customize which commit types trigger releases.

### Updating Different Version Files

If your version is stored elsewhere (e.g., `VERSION` file or `appsettings.json`), modify the `@semantic-release/exec` `prepareCmd` in `.releaserc.json` accordingly.

### Pre-release Branches

The template includes a pre-release branch configuration. Modify the `branches` section in `.releaserc.json` if needed.
