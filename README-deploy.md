# Schedule Sheet — deploy to iPhone & iPad

Same pattern as your expense tracker PWA: GitHub Pages hosts it, iOS installs it.

## 1 · Put it on GitHub Pages (once)

1. Create a new repository, e.g. `schedule-sheet` (public).
2. Upload everything in this folder to the repository root:
   `index.html · manifest.webmanifest · sw.js · icon-192.png · icon-512.png · apple-touch-icon.png`
3. Repo **Settings → Pages** → Source: *Deploy from a branch* → Branch: `main`, folder `/ (root)` → Save.
4. Wait a minute; your app is live at
   `https://<your-username>.github.io/schedule-sheet/`

## 2 · Install on iPhone / iPad (once per device)

1. Open that URL in **Safari** (must be Safari — Chrome on iOS can't install PWAs).
2. Tap **Share → Add to Home Screen → Add**.
3. Launch from the home-screen icon. Full screen, offline-capable, and your
   projects persist in that app's own storage.

## 3 · Things worth knowing

- **Data is per device.** The iPhone app, the iPad app, and your PC browser each
  keep their own copy. To move projects across devices, use **Export** on one and
  **Import** on the other (JSON travels fine through AirDrop or Files).
- **Keep backups anyway.** iOS can clear a web app's storage if you delete the
  icon (and, in some regions/settings, after very long disuse). Export after any
  serious planning session — it's one tap.
- **Updating the app:** replace `index.html` in the repo, and bump the version
  string at the top of `sw.js` (e.g. `schedule-sheet-v2`) so devices fetch the
  new build. Then close and reopen the app twice on the device.
- **Print/PDF for clients** works best from the desktop browser; on iPad,
  Share → Print from Safari also works.

## 4 · Touch controls (differences from desktop)

- Drag a bar with your finger to move its dates.
- Drag near a bar's **right end** to change its duration (the grab zone is wider on touch).
- Drag the **⠿ grip** to reorder tasks and phases.
- Rename via the **Name field** in the bottom strip (double-tap rename is
  unreliable on touch — the field always works).
- On iPhone, the Start/Due columns hide to fit the screen; the timeline and the
  Dur/% columns stay. Turn the phone landscape or use the bottom strip for full dates.

## 5 · Privacy model (read once)

- **Your schedule data never touches GitHub.** It lives only in each device's
  local storage; Export writes JSON directly to your device. The hosted file is
  just the empty app shell.
- **The app shell itself is public.** Anyone with the URL can open the (blank)
  app, and on a free plan the repo code is public too. That's fine — it contains
  no project data. Never commit your exported JSON files to the repo.
- **To load your real projects:** open your local `gantt-planner.html` on the PC,
  Export, then Import that JSON in the installed app on each device. The JSON
  travels by AirDrop/Files, not through GitHub.
- **Want a locked door as well?** Host the same folder on Cloudflare Pages and
  put Cloudflare Access (free tier) in front — it adds an email login gate.
  GitHub Pages has no access control on any plan.
