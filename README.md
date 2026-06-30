# Summer of AI GTM — Marketing LinkedIn Dashboard

A simple, visual dashboard for tracking LinkedIn post performance. Built as part of the **Summer of AI GTM** learning project.

No login. No database. No LinkedIn API. Just a CSV and a browser.

---

## How to Update Your Data Weekly

1. Go to **LinkedIn Analytics** → export your post data as a CSV.
2. Open the file in Excel or Google Sheets and make sure the column names match:
   - `Date`, `Time`, `Title`, `Impressions`, `Members Reached`, `Article Views`, `Reactions`, `Comments`, `Shares`, `URL`
3. Save the file as `linkedin-post.csv`.
4. In GitHub, go to the repository → click on `linkedin-post.csv` → click the pencil (Edit) icon → paste your new data → click **Commit changes**.
5. Vercel detects the commit and automatically redeploys the dashboard within about 30–60 seconds.
6. Refresh the dashboard URL — your new data is live.

That's it. No code required.

---

## How to Upload a CSV Directly in the Dashboard

The dashboard has an **Upload New CSV** button at the top.

- Click it and select your CSV file.
- A confirmation message will appear: *"This will delete and replace the current CSV data. Do you want to continue?"*
- Click **OK** to load the new data. Click **Cancel** to keep the current data.
- The dashboard refreshes instantly in your browser.

**Important:** This upload only updates the dashboard in your current browser session. It does not save the file to GitHub or permanently replace the data. When you refresh the page, the dashboard reloads from the original `linkedin-post.csv` file in GitHub.

To permanently update the data, follow the GitHub steps above.

---

## Engagement Rate Formula

The dashboard calculates engagement rate automatically for each post:

```
Engagement Rate = (Reactions + Comments + Shares) ÷ Impressions × 100
```

You do not need an Engagement Rate column in your CSV.

---

## How Vercel Keeps the Dashboard Fresh

This project is connected to GitHub. Every time you commit a change to the repository — including updating `linkedin-post.csv` — Vercel automatically rebuilds and redeploys the dashboard. There is nothing manual to do on Vercel's side.

**The workflow:**

```
Update CSV in GitHub → Commit change → Vercel redeploys → Dashboard shows updated data
```

---

## Future Version: Replace GitHub CSV from Dashboard

In Version 1, the **Upload New CSV** feature only updates the dashboard in your current browser session. It does not write back to GitHub.

To permanently replace the CSV from inside the dashboard (without going to GitHub directly), a future version would need:

- A **GitHub Personal Access Token** with `repo` write permission.
- A small backend function (e.g., a Vercel Serverless Function) that accepts the uploaded CSV, authenticates with GitHub using the token, and commits the new file to the repository via the GitHub API.
- This triggers a Vercel redeploy automatically, just like a manual commit would.

This is achievable in Version 2 and would complete the fully self-contained workflow:

```
Upload CSV in dashboard → GitHub commit via API → Vercel redeploys → Dashboard updates
```

For now, the GitHub manual update path works reliably and keeps the setup simple.

---

## Project Structure

```
/
├── index.html          ← The dashboard (single page, no build step)
├── linkedin-post.csv   ← Your LinkedIn post data
├── vercel.json         ← Vercel deployment configuration
└── README.md           ← This file
```

---

Built with Claude Code · Summer of AI GTM
