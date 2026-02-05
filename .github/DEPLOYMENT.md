# GitHub Pages Deployment Setup

This repository uses GitHub Actions to automatically build and deploy the VitePress documentation site to GitHub Pages.

## Automatic Setup

The deployment workflow (`.github/workflows/deploy.yml`) is configured to automatically enable GitHub Pages if it's not already enabled, using the `enablement: true` parameter in the `actions/configure-pages@v4` step.

When the workflow runs, it will:
- Automatically enable GitHub Pages if needed
- Configure Pages to use "GitHub Actions" as the source
- Build and deploy the VitePress site

The site will be available at: `https://datawhalechina.github.io/easy-pocket/`

## Workflow Triggers

The deployment workflow runs automatically when:
- Code is pushed to the `main` branch
- The workflow is manually triggered from the Actions tab

## Manual Setup (Optional)

If you prefer to manually enable GitHub Pages before the first workflow run:

1. Go to your repository on GitHub
2. Click on **Settings** (requires admin/write access)
3. Scroll down to the **Pages** section in the left sidebar
4. Under **Build and deployment**:
   - **Source**: Select "GitHub Actions"
   - This tells GitHub to use the workflow defined in `.github/workflows/deploy.yml`

5. Save the settings

## Troubleshooting

### Workflow Permissions

The workflow requires the following permissions to automatically enable Pages:
- `contents: read`
- `pages: write`
- `id-token: write`

These permissions are already configured in the workflow file.

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
