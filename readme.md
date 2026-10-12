# IG Follower Check

A **100% client-side** web tool that tells you which accounts you follow on
Instagram that don't follow you back.

No login. No server. No cookies. No data collection.

## How it works

Meta's official Instagram Graph API doesn't expose personal follower/following
lists. Third-party scrapers that log in with your credentials get accounts
banned. This tool takes a different approach:

1. You request your own data export from Meta (JSON format).
2. You drop the two JSON files into this page.
3. JavaScript computes `Following \ Followers` entirely in your browser.

Your files never leave your machine.

## Getting your data from Instagram

1. Instagram app → **Settings & Privacy** → **Accounts Center**
2. **Your information and permissions** → **Download your information**
3. Select **Some of your information** → check **Followers and following**
4. Format: **JSON**, Date range: **All time**
5. Wait 5–15 minutes for the download link
6. Extract the ZIP — you need `followers_1.json` and `following.json`

## 🧑‍💻 Local development

No build step. Just serve the folder:

```bash
# Python
python3 -m http.server 8000

# Node
npx serve .
```

Then open http://localhost:8000

## ☁️ Deploy to Vercel

### Option A — Vercel dashboard (easiest)

1. Push this repo to GitHub.
2. Go to [vercel.com/new](https://vercel.com/new) and import the repo.
3. Framework preset: **Other**. Leave build/output settings blank.
4. Click **Deploy**. Done.

### Option B — Vercel CLI

```bash
npm i -g vercel
vercel
```

## 📂 Project structure

```
.
├── index.html      # main app
├── privacy.html    # privacy policy
├── terms.html      # terms of use
├── vercel.json     # static hosting config
└── README.md
```

## ⚠️ Safety note on unfollowing

Don't mass-unfollow. Instagram rate-limits at roughly **30–50 unfollows per
hour** before issuing a temporary "Action Block". Spread cleanup across
multiple sessions.

## Legal

Not affiliated with Meta Platforms, Inc. or Instagram. See
[Terms](/terms.html) and [Privacy](/privacy.html).

## License

MIT — see [LICENSE](./LICENSE).
