# Timex AI Portal

A portal hosted on GitHub Pages for Timex Group AI programs.

- **Email check:** only company emails can get in (the domains are set in Admin Control).
- **Analytics:** how many times each app was opened, how many users used it, daily trend, and a list of users. You can export the raw log as CSV.
- **My Library:** each user can upload their own HTML tools, edit them, and submit them for publishing.
- **Admin Control:** upload, edit, reorder, hide and delete apps, publish them to GitHub, and review library submissions.

## Where your data is stored

Everything is stored in **your personal GitHub account**:

| Repo | Visibility | Holds |
|---|---|---|
| `<you>/timex-ai-portal` | Public (required for free GitHub Pages) | Website, `portal-config.json` (settings), `apps/*.html` |
| `<you>/ai-portal-data` | **Private** | `analytics/YYYY-MM/DD.json`, `library/<user>/…`, `submissions.json` |

## Setup with your GitHub account (about 5 minutes)

1. Unzip this folder. Open `index.html` in Chrome or Edge (just double-click it), enter your email, and go to **Admin Control**.
2. Click **Create token on GitHub**. It opens a classic token already set to the `repo` scope. Generate the token, paste it in, then click **Verify account**.
3. Keep the default repository names or change them, then click **Next**.
4. Choose this **timex-ai-portal** folder. Every file in it is uploaded.
5. Create a **separate data token**. Use a fine-grained token that can reach only `ai-portal-data`, with *Contents: Read and write*. The setup screen shows the exact steps. You can also skip this and add the token later in Admin Control → Data Storage.
6. Click **Create & publish**. The portal creates both repositories, uploads everything, turns on GitHub Pages and connects storage. Your site is ready at `https://<you>.github.io/timex-ai-portal/` after 1–2 minutes.

Already set up on another PC? In Admin Control, open **Already set up? Connect to an existing portal repository** and paste your token.

## Things to know

- **The email check is an entry form, not a password login.** Emails aren't verified. If the portal repo is public, anyone who knows the exact link to a file in `apps/` can open it without going through the portal. If an app contains confidential data, use a GitHub plan with private Pages (Enterprise Cloud), or host the portal internally.
- **The data token has to be in the public page**, because every user's browser writes its own visits. It's scrambled so GitHub's secret scanning doesn't revoke it, but someone determined can still pull it out. That's why it may only reach the private data repo. Rotate it from time to time: create a new token and publish it in Data Storage.
- **The admin token stays only in your browser** (local storage). It is never committed. A classic `repo` token can reach all your repositories, so click *Disconnect* on shared PCs. After setup you can switch to a fine-grained token limited to the portal repo (*Contents: Read and write*).
- **Updates go live in about a minute** after each publish, while GitHub Pages rebuilds.
- **File size:** each file must be under 100 MB (a GitHub limit). All users share the data token's limit of 5,000 GitHub API calls an hour, and one visit uses about 6 calls, so the portal handles roughly 800 recorded visits an hour.
- **Load from Data Folder:** for the AI Use Case Report's *Load from Data Folder* option, upload the tracker to `apps/data/AI_Master_Use_Case_Tracker.xlsx`. The *Upload from Computer* option always works.
