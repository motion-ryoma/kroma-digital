# Kroma Digital Website

Official website for Kroma Digital.

## Stack

- Astro
- GitHub
- Cloudflare Pages
- Production branch: `main`
- Current public URL: `https://kroma-digital.pages.dev/`

Cloudflare Pages is connected to this repository. A push to `main` triggers an automatic production deployment.

## Local project

```bash
cd ~/Projects/kroma-digital
```

Install dependencies if needed:

```bash
npm install
```

Run locally:

```bash
npm run dev -- --host
```

Production build check:

```bash
npm run build
```

## Safe update workflow

Before editing:

```bash
cd ~/Projects/kroma-digital
git pull
git status
```

After editing:

```bash
npm run build
git diff
git status
```

Only if the build succeeds:

```bash
git add .
git commit -m "Describe the change"
git push
```

After push, Cloudflare Pages deploys automatically.

## Main routes

```text
/
/about
/apps
/apps/khmer-expense-manager
/apps/khmer-seller-book
/blog
/contact
/privacy
/privacy/khmer-expense-manager
/privacy/khmer-seller-book
/terms
```

## Daily publishing workflow

Blog source files are stored in:

```text
src/content/blog/
```

Use this template:

```text
docs/templates/blog-post-template.md
```

Normal daily flow:

```text
1. Create one Markdown article in src/content/blog/
2. Set pubDate and draft: false
3. Run npm run build
4. Review git diff and git status
5. Commit and push
6. Cloudflare Pages publishes automatically
7. Reuse/shorten the article for the Kroma Digital Facebook post
```

The Home page automatically shows the latest published blog posts.

## Adding an app

Use:

```text
docs/templates/app-page-template.astro
docs/templates/app-privacy-template.astro
```

For each new app, normally create:

```text
src/pages/apps/<app-slug>.astro
src/pages/privacy/<app-slug>.astro
```

Then add the app to `/apps` and, when appropriate, the Home page.

Before using an app privacy-policy URL in Google Play, verify it against the final app implementation, including Android permissions, SDKs, analytics, advertising, storage, account/data deletion, network access, and Google Play Data safety declarations.

## Domain policy

An independent domain is optional for now. Continue using:

```text
https://kroma-digital.pages.dev/
```

A custom domain can be attached later without changing the GitHub/Astro publishing workflow.

## Important rule

Do not publish a change when `npm run build` fails. Fix the error first, then build again before committing or pushing.
