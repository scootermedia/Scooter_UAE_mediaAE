# Scooter Media website

Static website for Scooter Media. It has no runtime dependencies and builds to `dist/` for Cloudflare Pages, GitHub Pages, and Netlify.

## Local preview

```bash
npm run build
npm run preview
```

Open <http://localhost:8000>.

## Deploy with Cloudflare Pages

### Git integration

1. In Cloudflare, go to **Workers & Pages → Create → Pages → Connect to Git**.
2. Select this GitHub repository and use these build settings:
   - Production branch: `main`
   - Build command: `npm run build`
   - Build output directory: `dist`
3. Save and deploy. Every push to `main` will trigger a production deployment.

The checked-in `wrangler.jsonc` keeps the Pages project name, compatibility date, and output directory in source control. No environment variables are required.

### Wrangler CLI

After authenticating Wrangler, deploy the current build with:

```bash
npm run deploy:cloudflare
```

## Deploy with GitHub Pages

1. Create an empty GitHub repository and push this folder to its `main` branch.
2. In the repository, open **Settings → Pages**.
3. Set **Source** to **GitHub Actions**.

Every push to `main` then builds and deploys the site. The workflow is in `.github/workflows/deploy-pages.yml`.

## Deploy with Netlify

1. In Netlify, choose **Add new site → Import an existing project**.
2. Connect the GitHub repository.
3. Deploy the site.

Netlify reads `netlify.toml` automatically and runs:

- Build command: `npm run build`
- Publish directory: `dist`

No environment variables are required.
