# GitHub Pages Deployment Setup

This repository uses GitHub Actions to automatically build and deploy the VitePress documentation site to GitHub Pages.

## Initial Setup

Before the automated deployment workflow can run successfully, GitHub Pages must be enabled in the repository settings:

### Steps to Enable GitHub Pages

1. Go to your repository on GitHub
2. Click on **Settings** (requires admin/write access)
3. Scroll down to the **Pages** section in the left sidebar
4. Under **Build and deployment**:
   - **Source**: Select "GitHub Actions"
   - This tells GitHub to use the workflow defined in `.github/workflows/deploy.yml`

5. Save the settings

### After Enabling Pages

Once Pages is enabled, the deployment workflow will run automatically when:
- Code is pushed to the `main` branch
- The workflow is manually triggered from the Actions tab

The site will be available at: `https://datawhalechina.github.io/easy-pocket/`

## Troubleshooting

### Error: "Get Pages site failed"

If you see this error in the workflow logs:
```
Error: Get Pages site failed. Please verify that the repository has Pages enabled
```

This means GitHub Pages is not yet enabled. Follow the setup steps above.

### Error: "Resource not accessible by integration"

The default `GITHUB_TOKEN` does not have permissions to programmatically enable Pages. Pages must be manually enabled in repository settings first (see steps above).

## Workflow Details

The deployment workflow (`.github/workflows/deploy.yml`):
1. Checks out the code
2. Sets up Node.js
3. Configures Pages deployment settings
4. Installs dependencies
5. Builds the VitePress site
6. Uploads the built files as an artifact
7. Deploys to GitHub Pages

## Local Development

To preview the site locally:

```bash
npm install
npm run dev
```

Open http://localhost:5173/easy-pocket/ in your browser.
