# Experimental Programming in the Cognitive Sciences — Course Site

Quarto website for the 4-session jsPsych course (Master's Programme in Brain and Cognition).

## Structure

```
├── _quarto.yml          <- site configuration (navigation, theme)
├── index.qmd             <- homepage / course manual
├── materials.qmd          <- downloadable templates page
├── styles.css             <- minor styling tweaks
├── sessions/
│   ├── session1.qmd
│   ├── session2.qmd
│   ├── session3.qmd
│   └── session4.qmd
└── downloads/             <- the 4 session template .zip files
```

## Editing in RStudio

1. Open `jspsych-course.Rproj` in RStudio — this loads the folder as an RStudio Project.
2. RStudio detects the `_quarto.yml` and shows a **Render** button in the toolbar (and a **Build** pane). Click it, or run `quarto preview` in the RStudio Terminal tab, to preview the whole site locally with live reload.
3. Edit any `.qmd` file as plain text/Markdown. Re-render to see changes.

## Publishing to GitHub Pages

This repo is set up to publish via Quarto's built-in `gh-pages` workflow, which builds the site and pushes it to a `gh-pages` branch for you — no manual folder copying needed.

**One-time setup** (after this repo exists on GitHub and is cloned/connected in RStudio):

```bash
quarto publish gh-pages
```

Run this from the Terminal tab in RStudio, from the project root. The first time, it will:
- Ask you to confirm it's OK to publish.
- Create the `gh-pages` branch and push the rendered site to it.
- Add a small `_publish.yml` file to this repo, recording where it publishes to.

After that first run, go to the repo's **Settings → Pages** on GitHub and confirm the source is set to the `gh-pages` branch (Quarto usually configures this automatically, but it's worth checking once).

**Every time after that**, updating the live site is the same one command:

```bash
quarto publish gh-pages
```

## Day-to-day workflow

1. Edit `.qmd` files in RStudio.
2. Preview locally (`quarto preview` or the Render button) to check your changes.
3. Commit and push your source changes using RStudio's **Git** tab (or `git add`, `git commit`, `git push` in the Terminal) — this saves your edits to GitHub, but does **not** update the live site by itself.
4. Run `quarto publish gh-pages` to actually update the live site with your latest render.

Steps 3 and 4 are independent: you can commit/push source changes at any point, and (re-)publish whenever you're ready for the public site to reflect them.
