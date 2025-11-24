# Evidence Deployment Guide

## Vercel Deploy

```bash
# 1. Build locally
npm run build

# 2. Deploy from project root (not build directory)
vercel deploy --prod --yes --name=happiness-dashboard
```

**Deploy with token:**

```bash
VERCEL_TOKEN=your_token vercel deploy --prod --yes --name=happiness-dashboard
```

## Netlify Deploy

```bash
# 1. Build locally
npm run build

# 2. First deploy (create site)
netlify deploy --prod --dir=build --create-site

# 3. Subsequent deploys
netlify deploy --prod --dir=build
```

**Deploy with token:**

```bash
# First deploy
NETLIFY_AUTH_TOKEN=your_token netlify deploy --prod --dir=build --create-site

# Subsequent deploys
NETLIFY_AUTH_TOKEN=your_token netlify deploy --prod --dir=build
```

## Important Notes

- Evidence is a static site generator, must build **locally**
- Build output is in `build/` directory
- Do not let Vercel/Netlify rebuild the project
