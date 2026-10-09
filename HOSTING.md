# Hosting Netsim for students

Netsim is a fully static site (no server code, no database, no login). Student progress (completed levels and the packets they have built) is saved in each student's own browser `localStorage`, so:

- Progress is per browser and per device. Clearing site data/history, using private browsing, or switching browsers/computers resets it.
- Students sharing a computer and browser profile share progress.
- You cannot see student progress centrally.

Any static host works. The files must be served over HTTP(S); opening `index.html` directly from disk (`file://`) will not work.

## Option 1: GitHub Pages (recommended, free)

1. Push this repository to GitHub (e.g. `MrRoush/netsim`).
2. Merge the branch containing these changes into your default branch (e.g. `main`).
3. In the repository go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to **Deploy from a branch**, choose `main` and folder `/ (root)`, then **Save**.
5. Wait 1–2 minutes. The site will be at `https://<your-username>.github.io/netsim/` (e.g. `https://mrroush.github.io/netsim/`). The URL is shown at the top of the Pages settings.
6. Give students that URL.

Notes:
- GitHub Pages sites are public. There is nothing secret in the site.
- Updates: merge/push to the branch and Pages redeploys automatically.
- To take it down: **Settings → Pages → Unpublish site**.

## Option 2: Netlify Drop (no GitHub needed)

1. Download or clone the repo.
2. Go to <https://app.netlify.com/drop> and drag the project folder onto the page.
3. Share the generated `*.netlify.app` URL. Delete the site later from the Netlify dashboard.

## Option 3: School or local web server

Copy all files to any web server folder (Apache, nginx, IIS, ...). For a quick classroom demo from your own machine:

```
python3 -m http.server 8000
```

Students on the same network can browse to `http://<your-ip>:8000/`.

## Testing

Open the site, check that the level list loads with thumbnails, start "Getting started", and confirm the game canvas appears. Complete a level, return to the list, and confirm it shows a checkmark; reloading should keep it.

## Resetting progress

In the browser developer console on the site run `localStorage.clear()`, or clear the site's data in the browser settings.
