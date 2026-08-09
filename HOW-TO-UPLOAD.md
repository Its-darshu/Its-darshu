# How to make your live 3D profile — upload steps

This folder is a **ready-to-upload profile repo** for `Its-darshu`, set up exactly
like https://github.com/yoshi389111/yoshi389111 .

## What's inside
```
Its-darshu/
├─ README.md                         # your profile page; 3D chart embedded at the bottom
├─ .github/
│  ├─ workflows/profile-3d.yml       # the daily "live fetch" GitHub Action
│  └─ green-dual.json                # the green light/dark template (identical to yoshi's)
└─ profile-3d-contrib/
   └─ profile-green-dual.svg         # PLACEHOLDER (shows sample data until the Action runs once)
```

## How the "live" part works
`profile-green-dual.svg` is a static picture. It cannot fetch data itself.
The **GitHub Action** (`profile-3d.yml`) runs every day on GitHub's servers,
pulls YOUR contribution data from GitHub, re-draws the SVG, and commits it back.
No personal token needed — GitHub gives the Action its own `secrets.GITHUB_TOKEN`
automatically.

---

## Upload steps

### 1. Create your profile repo
- Go to https://github.com/new
- Repository name: **`Its-darshu`** (must exactly match your username)
- **Public**, and tick **Add a README file**
- Create repository.
> If it already exists, just use it.

### 2. Upload these files
Easiest way (website):
- Open the `Its-darshu` repo → **Add file → Upload files**
- Drag in **`README.md`** and the **`profile-3d-contrib`** folder.
- Commit.
- ⚠️ GitHub's web uploader can't create the hidden `.github` folder by drag-drop.
  Add those two files manually instead:
  1. **Add file → Create new file**, name it exactly `.github/workflows/profile-3d.yml`,
     paste the contents of that file from here, commit.
  2. **Add file → Create new file**, name it exactly `.github/green-dual.json`,
     paste the contents of that file from here, commit.

  (Or, if you use Git on your PC: copy everything in this `Its-darshu` folder into
  the cloned repo and `git add . && git commit -m "setup" && git push` — the
  `.github` folder uploads normally that way.)

### 3. Let the Action write to your repo
- Repo **Settings → Actions → General → Workflow permissions**
- Choose **Read and write permissions** → **Save**

### 4. Generate your real chart now (don't wait a day)
- Repo **Actions** tab → left sidebar **GitHub-Profile-3D-Contrib**
- **Run workflow → Run workflow**
- Wait ~1 minute. It overwrites the placeholder with YOUR real data.

### 5. Done
Open https://github.com/Its-darshu — your 3D contribution calendar shows at the
bottom of your profile and refreshes automatically every day. 🎉

## Optional tweaks
- Change refresh time: edit the `cron:` line in `profile-3d.yml` (it's in UTC).
- Want a different style/colors: edit `.github/green-dual.json`.
