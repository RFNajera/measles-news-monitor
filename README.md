# Measles News Monitor

A static GitHub Pages dashboard that displays recent measles-related news and refreshes hourly with GitHub Actions.

## What is included

- A polished GitHub Pages front end
- A scheduled GitHub Action that runs every hour
- A Node script that fetches Google News RSS results for `measles`
- Deduplication and source classification
- Local JSON output at `data/news.json`

## Before you deploy

1. Create a new GitHub repository.
2. Upload all files from this package.
3. In `index.html`, replace `https://YOUR-USERNAME.github.io/YOUR-REPO/` in the `og:url` meta tag.
4. Commit to your default branch.
5. In GitHub, go to **Settings > Pages** and set the site to deploy from the default branch.
6. In GitHub, go to **Actions** and allow workflows if prompted.
7. Run the **Update measles news** workflow once manually from the Actions tab.

## Notes

- The workflow runs at minute 17 of every hour in UTC.
- Scheduled workflows run from the default branch.
- If your repository is private, GitHub Pages behavior depends on your plan and settings.

## Customizing blocked sources

Edit `BLOCKED_DOMAINS` in `scripts/update-news.js`.

## Customizing the schedule

Edit `.github/workflows/update-news.yml`.

Current cron:

```yaml
- cron: "17 * * * *"
```

## Local testing

```bash
npm install
npm run update-news
python3 -m http.server 8000
```

Then open `http://localhost:8000/`.
