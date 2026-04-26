# Study Plan Bridge

A daily study planner built on intention-behavior gap research (Gollwitzer & Sheeran, Sheeran & Webb, Sirois & Pychyl). Pure static HTML — no build step, no server, no dependencies. Your data stays in your browser's localStorage.

## Files

- `index.html` — the whole app, single file
- `README.md` — this file

## Run it locally (two options)

### Option 1 — Just open the file
Double-click `index.html`. It opens in your default browser and works fully. Done.

### Option 2 — Local web server (recommended for daily use)
Some browser features behave better over `http://` than `file://`. Pick whichever you have:

```bash
# Python (built into macOS)
cd study-plan-app
python3 -m http.server 8000
# Now open http://localhost:8000

# Or Node
npx serve .
```

## Put it on GitHub and deploy via GitHub Pages

This gives you a free public URL like `https://your-username.github.io/study-plan-bridge/` that you can bookmark on your phone and laptop.

### One-time setup

1. Create an empty repo on github.com — call it `study-plan-bridge` (or whatever). Don't tick "add README" — you already have one.

2. In a terminal, from inside the `study-plan-app` folder:

   ```bash
   cd "/Users/dan/Documents/respaper/study-plan-app"
   rm -rf .git              # in case a stale .git folder is here
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/study-plan-bridge.git
   git push -u origin main
   ```

   Replace `YOUR-USERNAME` with your GitHub username.

3. Enable Pages: on the repo page, go to **Settings → Pages**. Under "Build and deployment", set **Source** to `Deploy from a branch`, **Branch** to `main` and folder to `/ (root)`. Save.

4. Wait ~1 minute. Your URL will appear at the top of the Pages settings page.

### Updating later

After you edit `index.html`:

```bash
git add index.html
git commit -m "Tweak"
git push
```

GitHub Pages re-deploys automatically.

## Where does my data live?

In your browser's `localStorage` under the key `studyPlanBridge_v1`. It's per-browser per-device — your phone and laptop won't sync. If you clear browser storage, your history is gone.

If you want sync across devices later, the cleanest upgrade path is to swap the `localStorage` calls in the script for a tiny backend (Cloudflare Workers + KV, or a Supabase project). Both have free tiers. The current code keeps `loadState`/`saveState` in two functions at the top of the script for exactly this reason.

## Credit

Built from four papers on the intention-behavior gap:

- Sheeran & Webb (2016), *The Intention-Behavior Gap*
- Sheeran (2002), *Intention-Behaviour Relations*
- Gollwitzer & Sheeran (2006), *Implementation Intentions and Goal Attainment*
- Sirois & Pychyl (2013), *Procrastination and Short-Term Mood Regulation*
