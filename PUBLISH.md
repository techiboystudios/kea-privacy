# How to publish this

`index.html` is the page people see. `README.md` is the same policy in Markdown so the repo front
page is readable too. Keep them in step if you edit one.

This folder is **already a git repo** with one commit and the remote set to
`https://github.com/techiboystudios/kea-privacy.git`. All that is missing is permission to push.

## Why it is not pushed already

The `gh` CLI on this machine is signed in as **essentialdeepanshu**, and `techiboystudios` is a
separate GitHub user account rather than an organisation that account belongs to. One account cannot
create a repo under another without being given access.

## Finish it, one of two ways

### A. Sign in as techiboystudios (recommended)

```bash
gh auth login                       # choose GitHub.com, HTTPS, sign in as techiboystudios
gh repo create techiboystudios/kea-privacy --public --source=. --remote=origin --push
```

That creates the repo and pushes in one step. To go back to the other account afterwards:
`gh auth switch`.

### B. Create it in the browser

Make a new **public** repo at <https://github.com/new> called `kea-privacy` under the
techiboystudios account, leaving it empty (no README, no licence), then:

```bash
cd ~/Desktop/kea-privacy
git push -u origin main
```

## Then turn on Pages

In the repo: **Settings → Pages → Source: Deploy from a branch → Branch `main`, folder `/ (root)`
→ Save.** Give it a minute.

Your URL will be:

```
https://techiboystudios.github.io/kea-privacy/
```

`index.html` at the root means the URL renders as a real page with no Jekyll theme or config needed.
Open it in a browser and confirm it loads before pasting it into Play.

## Where the link goes in Play Console

- **App content → Privacy policy → Privacy policy URL**
- **Store listing → Store settings → Website** (optional, the same URL is fine)

## Before you publish

- The repo must be **public**. GitHub Pages will not serve a private repo on a free account, and
  Play has to be able to fetch the URL.
- The contact address is **techiboystudios@gmail.com** and is visible to anyone who opens the page.
  It appears once in `index.html` and once in `README.md`.

## Keeping it accurate

The source of truth lives in the app repo at `docs/PRIVACY.md`. If the app gains a permission or an
action that touches data, change it there and copy it here. A policy that no longer matches the
app's permissions is worse than no policy, and Play does check.
