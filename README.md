# Clinical Neurology Simulators

Interactive simulators for clinical neurology. Plain HTML, CSS and JavaScript: no build step, no dependencies. The only external request is Google Fonts (IBM Plex), and the pages fall back to system fonts without it.

## Layout

```
index.html                 landing page (list of simulators, search, topic filter)
visual-pathway/index.html
extraocular/index.html
brachial-plexus/index.html
```

Each simulator is one self-contained HTML file in its own folder, so its address is `<site>/<folder>/`.

## Run locally

Open `index.html` in a browser. To serve it the way GitHub Pages does:

```
python3 -m http.server 8000
```

then go to http://localhost:8000.

## Publish with GitHub Pages

1. Create a new repository on GitHub (public, unless you have a plan that allows Pages on private repositories).
2. Upload the contents of this folder to the repository root, so `index.html` sits at the top level.
3. In the repository, go to Settings, then Pages. Under "Build and deployment", set Source to "Deploy from a branch", choose the `main` branch and the `/ (root)` folder, and save.
4. After a minute or two the site is at `https://<your-username>.github.io/<repository-name>/`.

## Publish simulators one at a time

The landing page only lists entries in `SIMS` that are not marked `live: false`. `visual-pathway` is live; `extraocular` and `brachial-plexus` are hidden. To publish one, commit its folder, delete its `live: false` line in `index.html`, and push.

## Add a simulator

1. Create a folder, for example `basal-ganglia/`, and put the page in `basal-ganglia/index.html`.
2. Add a "&larr; All simulators" link to the page header: `<a class="home" href="../">&larr; All simulators</a>`.
3. Add one entry to the `SIMS` array near the bottom of the root `index.html` (path, title, blurb, tags, features).
4. Commit and push. Pages redeploys on its own.

## Notes

- The simulators are teaching tools. Each page has a "How the model works, and what it leaves out" section.
- The pages use relative links only, so the site works under a repository sub-path as well as on a custom domain.
