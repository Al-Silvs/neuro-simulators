# Clinical Neurology Simulators

Interactive simulators for clinical neurology. Plain HTML, CSS and JavaScript: no build step, no dependencies. The only external request is Google Fonts (IBM Plex), and the pages fall back to system fonts without it.

## Layout

```
index.html                 landing page (simulators grouped by section)
visual-pathway/index.html
basal-ganglia/index.html
brachial-plexus/index.html
emg-ncs/index.html
extraocular/index.html
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
3. In the repository, go to Settings, then Pages. Under "Build and deployment", set Source to "Deploy from a branch", choose the `master` branch (the branch this repository uses) and the `/ (root)` folder, and save.
4. After a minute or two the site is at `https://<your-username>.github.io/<repository-name>/`.

This repository is `Al-Silvs/neuro-simulators`, deployed from `master` at `/`. Live site: https://al-silvs.github.io/neuro-simulators/

## Publish simulators one at a time

The landing page lists every entry in `SIMS` (near the bottom of `index.html`) that is not marked `live: false`. Live now: visual pathway, extraocular movements, basal ganglia, brachial plexus, EMG and nerve conduction. None are hidden. To publish one, commit its folder, delete its `live: false` line, and push.

## Add a simulator

1. Create a folder, for example `basal-ganglia/`, and put the page in `basal-ganglia/index.html`.
2. Add a "&larr; All simulators" link to the page header: `<a class="home" href="../">&larr; All simulators</a>`.
3. Add one entry to `SIMS` in the root `index.html`: `path`, `section`, `glyph`, `title`, `blurb` (one or two sentences) and `features` (three short items).
   - `section` must be a name in the `SECTIONS` list. Add a new name there (for example `'Epilepsy'`) to start a new group; empty sections are not shown.
   - `glyph` is a key in `GLYPHS` (`fields`, `eye`, `circuit`, `plexus`, `cmap`). Add a new 40×40 line drawing there, or leave the key out for a blank tile.
4. Commit and push. Pages redeploys on its own.

## Notes

- The simulators are teaching tools. Each page has a "How the model works, and what it leaves out" section.
- The pages use relative links only, so the site works under a repository sub-path as well as on a custom domain.
