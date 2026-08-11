# Setup — Khayden's Profile Repo

One-time steps to get everything live.

## 1. Create the special "profile" repo on GitHub

1. Go to https://github.com/new
2. **Repository name**: `KhaydenChetty` (must exactly match your username — case-sensitive)
3. **Public** (required for the README to render on your profile)
4. Tick **"Add a README file"** — GitHub will show a green banner *"You found a secret!"*. That's the magic repo.
5. Create.

## 2. Push this scaffold

From this directory (`C:\Claude projects\github_Profile`):

```bash
git init
git branch -M main
git add .
git commit -m "feat: cyberpunk profile scaffold"
git remote add origin https://github.com/KhaydenChetty/KhaydenChetty.git
git pull origin main --allow-unrelated-histories  # merge the GitHub-created README
# resolve any conflict by keeping OUR README.md, then:
git push -u origin main
```

## 3. Create the METRICS_TOKEN (personal access token)

The `lowlighter/metrics` action needs a PAT to read your public profile stats.

1. Go to https://github.com/settings/tokens?type=beta (fine-grained tokens)
2. **Generate new token** → name it `METRICS_TOKEN`
3. **Expiration**: 1 year (renew yearly)
4. **Resource owner**: your account
5. **Repository access**: All repositories (needed so metrics can count private-repo contributions if `count_private: yes`)
6. **Permissions** (Account permissions):
   - `Profile` → Read & Write (only if using plugins that write, otherwise Read)
7. **Permissions** (Repository permissions):
   - `Contents` → Read & Write (to commit generated SVGs back)
   - `Metadata` → Read-only (default)
8. Generate & **copy the token**.
9. In your `KhaydenChetty/KhaydenChetty` repo → **Settings → Secrets and variables → Actions → New repository secret**:
   - Name: `METRICS_TOKEN`
   - Value: paste the token

> The `snake` and `3d-contrib` workflows use the built-in `GITHUB_TOKEN` — no extra setup.

## 4. Trigger the workflows once manually

Wait for the first push to finish, then:

- **Actions** tab in your repo
- For each workflow (Metrics, Generate Snake Animation, GitHub Profile 3D Contrib) → **Run workflow** → main → Run.

After ~1–2 min each, you'll have:
- `metrics.plugin.*.svg` committed to `main`
- `profile-3d-contrib/profile-night-rainbow.svg` committed to `main`
- `github-snake.svg` + `github-snake-dark.svg` on the `output` branch

Your `README.md` already points to all of these — refresh your profile page and it's live.

## 5. What auto-refreshes going forward

| Workflow    | Schedule            | Output                                      |
|-------------|---------------------|---------------------------------------------|
| metrics     | every 6 hours       | all `metrics.plugin.*.svg` on `main`         |
| snake       | daily               | `github-snake*.svg` on `output` branch       |
| 3d-contrib  | daily 18:00 UTC     | `profile-3d-contrib/*.svg` on `main`         |

Everything else in the README (skillicons, github-readme-stats, streak-stats, trophies, activity graph, quote, capsule header/footer) is rendered on-demand by hosted services — nothing to maintain.

## 6. Tweaks you might want later

- **Add LinkedIn / X / portfolio badges**: uncomment/extend the socials block in `README.md`.
- **Change the accent colors**: search for `00FFF0` (cyan), `FF00FF` (magenta), `8338EC` (purple), `FF006E` (pink) in `README.md` and swap.
- **Different 3D style**: the yoshi389111 action outputs several — `profile-night-view.svg`, `profile-green-animate.svg`, `profile-south-season-animate.svg`, etc. Swap the filename in the README's 3D block.
- **Add wakatime**: sign up at wakatime.com, install the plugin in Android Studio/VS Code, then add a wakatime card block (I can wire it up later).

## 7. Troubleshooting

- **SVGs 404 on the profile page for a few minutes after first push** → GitHub's raw CDN caches. Hard-refresh or wait ~5 min.
- **Metrics workflow fails with "Bad credentials"** → your `METRICS_TOKEN` secret is missing or expired.
- **Snake workflow's push fails** → repo Settings → Actions → General → Workflow permissions → set to **Read and write permissions**.
- **3D contrib commits nothing** → normal on days you had zero contributions; the SVG just won't change.
