# Publishing your Lovable project to GitHub Pages

## Fix applied

- **`vite.config.ts`** in your Lovable project (`cesar-portfolio`) was fixed: the file was overwritten with a valid config (correct plugin `@vitejs/plugin-react-swc`, no null bytes). You can run `npm run build` there now.

## Option A: Deploy from this repo (recommended)

1. Copy your **entire Lovable project** (from `cesar-portfolio`) into an **`app`** folder in this repo:
   ```bash
   # From the folder that contains both repos:
   cp -R cesar-portfolio/* cesar-dx.github.io/app/
   cp cesar-portfolio/package.json cesar-dx.github.io/app/
   cp cesar-portfolio/package-lock.json cesar-dx.github.io/app/
   # Copy other root files: index.html, tsconfig.json, tailwind.config.js, etc.
   ```

2. In GitHub: **Settings → Pages** → Source: **GitHub Actions**.

3. Push to `main`. The workflow will build the app from `app/` and deploy to GitHub Pages.

## Option B: Deploy built files manually

1. In your Lovable project folder:
   ```bash
   cd /Users/cesardori/Documents/cesar-portfolio
   npm run build
   ```

2. Copy the **contents** of `cesar-portfolio/dist/` into the **root** of this repo (e.g. into `cesar-dx.github.io`), so that `index.html` and `assets/` are at the root.

3. Commit and push to `main`. If this repo is set as your GitHub Pages site, it will serve the built app.

## If the app is already at the root of this repo

If you later move the Lovable app to the **root** of this repo (no `app/` folder), update `.github/workflows/deploy.yml`: remove the `cd app` and use `path: dist` instead of `path: app/dist`, and set `cache-dependency-path: package-lock.json`.
