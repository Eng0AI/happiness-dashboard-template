# Evidence Deployment Guide

## Vercel Deploy

```bash
# 1. Install dependencies
npm install

# 2. Run data sources (fetches/processes data)
npm run sources

# 3. Build the site
npm run build

# 4. Deploy from project root (not build directory)
vercel deploy --prod --yes
```

**Deploy with token:**

```bash
VERCEL_TOKEN=your_token npm run sources && npm run build && vercel deploy --prod --yes
```

## Netlify Deploy

```bash
# 1. Install dependencies
npm install

# 2. Run data sources
npm run sources

# 3. Build the site
npm run build

# 4. First deploy (create site)
netlify deploy --prod --dir=build --create-site

# 5. Subsequent deploys
netlify deploy --prod --dir=build
```

**Deploy with token:**

```bash
# First deploy
NETLIFY_AUTH_TOKEN=your_token npm run sources && npm run build && netlify deploy --prod --dir=build --create-site

# Subsequent deploys
NETLIFY_AUTH_TOKEN=your_token npm run sources && npm run build && netlify deploy --prod --dir=build
```

## Important Notes

### Why Build Locally?

Evidence is a static site generator that must be built locally because:
- Running `npm install` on Vercel can timeout (40+ minutes due to DuckDB compilation)
- Node.js v22+ has compatibility issues with DuckDB
- Local builds are faster and more reliable

### Build Process Explained

1. **`npm install`** - Install dependencies (use Node 18-20)
2. **`npm run sources`** - Fetch and process data from sources
3. **`npm run build`** - Generate static HTML/CSS/JS in `build/` directory
4. **Deploy** - Upload `build/` directory to hosting platform

### vercel.json Configuration

The project includes `vercel.json` with:
```json
{
  "buildCommand": "",
  "outputDirectory": "build",
  "framework": null
}
```

- `"buildCommand": ""` - Tells Vercel to skip building (we build locally)
- `"outputDirectory": "build"` - Deploy files from `build/` directory
- `"framework": null` - Don't auto-detect framework

### Troubleshooting

**If deployment fails:**
1. Check Node version: `node --version` (must be 18-20, not 22+)
2. Clean install: `rm -rf node_modules package-lock.json && npm install`
3. Verify build succeeds: `npm run sources && npm run build`
4. Check `build/index.html` exists before deploying
