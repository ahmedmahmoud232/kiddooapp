# KiddoApp Landing Page — Deployment Guide

This repo contains a static landing page (`index.html`) for KiddoApp. Below are concise steps to publish it globally and options you can pick from.

Important: replace placeholder assets (`/og-image.png`, `/favicon.ico`) and update `sitemap.xml` with your real domain before publishing.

Quick local preview

Open PowerShell in the project folder:

```powershell
# Serve locally on port 8000
python -m http.server 8000
# then open http://localhost:8000 in your browser
```

Option A — Netlify (recommended for static sites)

1. Create a GitHub repository and push your files (see commands below).
2. Sign in to https://app.netlify.com and choose "New site from Git".
3. Connect your GitHub repo and branch (default: `main`).
4. Set the build command to empty (no build) and the publish directory to `/` (or leave empty; Netlify will publish files from the repository root).
5. Add your custom domain in Netlify and update DNS records as instructed. Netlify provisions free HTTPS automatically.
6. (Optional) Use the included `netlify.toml` for redirects or headers.

Option B — GitHub Pages (simple and free)

1. Create a GitHub repository and push your files.
2. In the repo Settings > Pages, set Source to `main` branch / root (or use the workflow below to deploy automatically).
3. Configure your domain with a `CNAME` file (if you have one) and update DNS records. GitHub Pages provides HTTPS for apex/subdomains via Let’s Encrypt.

Option C — Vercel

1. Sign in to https://vercel.com, import your GitHub repo and deploy.
2. Vercel will detect no-build static site and publish it. Add a custom domain in the Vercel dashboard.

PowerShell: create repo & push (one-time)

```powershell
# run in project root (c:\Users\Ahmed\Desktop\New folder (5))
git init
git add .
git commit -m "Initial landing page"
# create a new GitHub repo called kiddo-landing via the GitHub web UI or CLI
git branch -M main
git remote add origin https://github.com/yourusername/kiddo-landing.git
git push -u origin main
```

Automated GitHub Pages workflow (optional)

A GitHub Actions workflow provided in `.github/workflows/pages-deploy.yml` will upload site contents and publish via GitHub Pages whenever you push to `main`.

Domain & SSL tips

- On Netlify/Vercel: add your custom domain and follow their DNS instructions; SSL is automatic.
- On GitHub Pages: add a `CNAME` file with your domain and update DNS to point to GitHub Pages IPs or use a CNAME record.

Forms & newsletter

The newsletter form is client-side for now. You can integrate it with:
- Netlify Forms (no server): add `netlify` attributes to the form (I can implement this), or
- Formspree / Getform / Mailchimp: replace form `action` with the provider endpoint.

Next steps I can do for you (pick one):
- Wire newsletter form to Netlify Forms and add success/error UX. 
- Add server-backed persistence for Quick Todo and user accounts (requires a backend).
- Connect the site to Netlify and configure a custom domain (I can prepare DNS entries to add to your registrar).

If you want me to proceed with a specific provider (Netlify, Vercel, GitHub Pages), tell me which one and your repo / domain name and I'll continue and apply the exact configuration and optional DNS/CNAME file.
