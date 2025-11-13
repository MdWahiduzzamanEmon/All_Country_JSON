# Publishing to NPM

This guide explains how to publish the `all-country-json` package to NPM.

## Prerequisites

1. **NPM Account**: Create an account at [npmjs.com](https://www.npmjs.com/signup)
2. **NPM CLI**: Ensure you have Node.js and npm installed
3. **Repository Access**: You must be a maintainer of this repository

## One-Time Setup

### 1. Login to NPM

```bash
npm login
```

Enter your NPM credentials when prompted.

### 2. Verify Login

```bash
npm whoami
```

This should display your NPM username.

## Publishing Steps

### Manual Publishing

#### 1. Update Version (if needed)

Edit `package.json` and update the version number following [Semantic Versioning](https://semver.org/):
- **Patch release** (bug fixes): `1.0.0` → `1.0.1`
- **Minor release** (new features): `1.0.0` → `1.1.0`
- **Major release** (breaking changes): `1.0.0` → `2.0.0`

Or use npm:
```bash
# For patch release
npm version patch

# For minor release
npm version minor

# For major release
npm version major
```

#### 2. Test the Package Locally

```bash
# Run the test script
npm test

# Check which files will be published
npm pack --dry-run
```

#### 3. Publish to NPM

```bash
npm publish
```

For the first publish, if the package name is scoped or you want to make it public:
```bash
npm publish --access public
```

#### 4. Verify Publication

Visit your package page: `https://www.npmjs.com/package/all-country-json`

Or install it to test:
```bash
npm install all-country-json
```

### Automated Publishing (Recommended)

This repository includes a GitHub Actions workflow that automatically publishes to NPM when you create a new release.

#### Setup GitHub Secrets

1. Go to your repository on GitHub
2. Navigate to **Settings** → **Secrets and variables** → **Actions**
3. Click **New repository secret**
4. Create a secret named `NPM_TOKEN` with your NPM access token

**To get your NPM token:**
```bash
npm login
npm token create --read-only=false
```
Copy the generated token and paste it as the `NPM_TOKEN` secret value.

#### Create a Release

1. Go to the repository on GitHub
2. Click **Releases** → **Create a new release**
3. Create a new tag (e.g., `v1.0.0`)
4. Fill in the release title and description
5. Click **Publish release**

The GitHub Actions workflow will automatically:
- Run tests
- Publish the package to NPM
- Update the version

## Updating the Package

When you need to update the data or make changes:

1. Make your changes to the repository
2. Update the version in `package.json`
3. Commit your changes
4. Create a new Git tag:
   ```bash
   git tag v1.0.1
   git push origin v1.0.1
   ```
5. Create a GitHub release (for automated publishing)

Or publish manually:
```bash
npm version patch
npm publish
git push --follow-tags
```

## Best Practices

- **Always test before publishing**: Run `npm test` and `npm pack --dry-run`
- **Use semantic versioning**: Follow [semver](https://semver.org/) guidelines
- **Update CHANGELOG**: Document changes in each version
- **Tag releases**: Create Git tags for each published version
- **Review files**: Check `.npmignore` to ensure only necessary files are published

## Troubleshooting

### "You do not have permission to publish"
- Ensure you're logged in: `npm whoami`
- The package name might be taken. Try a different name in `package.json`

### "This package has been marked as deprecated"
- You may have accidentally deprecated it. Contact NPM support or use a new version.

### "Version already exists"
- You must increment the version number before publishing again
- Use `npm version patch|minor|major` to update the version

## Files Included in Package

The following files are included in the NPM package (see `package.json` → `files`):
- `All_Country.json` - The main data file
- `README.md` - Documentation
- `LICENSE` - MIT license

Files excluded (via `.npmignore`):
- Development files (example.html, etc.)
- Git files (.git, .gitignore)
- CI/CD files (.github)

## Resources

- [NPM Publishing Documentation](https://docs.npmjs.com/packages-and-modules/contributing-packages-to-the-registry)
- [Semantic Versioning](https://semver.org/)
- [NPM CLI Commands](https://docs.npmjs.com/cli/v8/commands)
