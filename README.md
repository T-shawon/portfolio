# Portfolio — deploy to Vercel

This repo contains a static portfolio site. Below are quick steps to publish on Vercel and enable CI/CD via GitHub Actions.

1) Create GitHub repo and push

```bash
cd "/Users/mohammadnabi/Developer/Project 01/portfolio"
git init
git add .
git commit -m "Initial commit"
git branch -M main
gh repo create YOUR_USERNAME/REPO_NAME --public --source=. --remote=origin --push
```

2) Option A — Connect via Vercel UI (recommended)
- Go to https://vercel.com, sign in with GitHub and import the repository.
- Choose the `main` branch and set Framework Preset to **Other** / static.
- Vercel will auto-deploy on every push.

3) Option B — Use GitHub Actions (workflow included)
- Create a Vercel token: Vercel Dashboard → Settings → Tokens → New Token.
- In your GitHub repo Settings → Secrets → Actions, add `VERCEL_TOKEN` with that token.
- The included workflow `.github/workflows/deploy-vercel.yml` runs `vercel --prod` on pushes to `main`.

Notes
- If this is your first time deploying, run `vercel` locally once to link the project (`vercel link`) so the CLI recognizes the project settings. The workflow will also work if you provide `VERCEL_TOKEN` and have linked the project at least once.
- For the easiest setup and continuous deployments, connecting your GitHub repository in the Vercel UI is the simplest.
