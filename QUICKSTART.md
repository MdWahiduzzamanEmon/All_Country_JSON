# Quick Start: Publishing to NPM

This is a quick guide to publish the `all-country-json` package to NPM for the first time.

## Prerequisites

You need an NPM account. If you don't have one:
1. Go to [npmjs.com/signup](https://www.npmjs.com/signup)
2. Create an account

## First-Time Publishing (Manual)

### Step 1: Login to NPM

```bash
npm login
```

Enter your credentials when prompted.

### Step 2: Publish

```bash
npm publish --access public
```

That's it! Your package will be published to NPM and available at:
- https://www.npmjs.com/package/all-country-json

### Step 3: Verify

Install the package to test:
```bash
npm install all-country-json
```

## Future Updates

For subsequent releases, you can use the automated GitHub Actions workflow:

### Option A: Automated via GitHub Release (Recommended)

1. **Setup NPM Token** (one-time):
   - Run: `npm token create --read-only=false`
   - Copy the token
   - Go to GitHub repo → Settings → Secrets and variables → Actions
   - Create a secret named `NPM_TOKEN` and paste the token

2. **Create a Release**:
   - Update version in `package.json` (e.g., `1.0.1`)
   - Commit and push changes
   - Go to GitHub repo → Releases → Create a new release
   - Create a new tag (e.g., `v1.0.1`)
   - Publish release
   - GitHub Actions will automatically publish to NPM

### Option B: Manual Update

```bash
# Update version
npm version patch  # or minor, or major

# Publish
npm publish

# Push the version commit and tag
git push --follow-tags
```

## Need More Help?

See [PUBLISHING.md](PUBLISHING.md) for detailed documentation.

## Troubleshooting

**Error: "package name already taken"**
- The package name might be taken by someone else
- Try a different name in `package.json` (e.g., `@yourusername/all-country-json`)

**Error: "You do not have permission"**
- Make sure you're logged in: `npm whoami`
- For scoped packages, use: `npm publish --access public`

**Error: "Version already exists"**
- Increment the version in `package.json` before publishing again
