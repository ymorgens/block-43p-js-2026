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
2. RStudio has its **own built-in copy of Quarto**, bundled with the IDE itself (since RStudio 2022.07) — this is separate from the standalone Quarto CLI, and works even if a system-wide `quarto` command isn't installed or isn't on your PATH. This means the **Render** button in the toolbar, and the **Preview** button on any `.qmd` file, should work locally regardless of whether `quarto` runs in the Terminal.
3. Edit any `.qmd` file as plain text/Markdown. Click **Render** to preview your changes.

::: {.callout-note}
If the Render button *also* doesn't work, check **Tools → Global Options → Quarto** in RStudio — there's a setting there showing which Quarto installation RStudio is using, which can help diagnose the issue further.
:::

## Publishing to GitHub Pages (no local Quarto install needed)

This repo publishes itself automatically, using a GitHub Actions workflow (`.github/workflows/publish.yml`) that renders and deploys the site entirely on GitHub's own servers. **Your machine never needs Quarto installed for this to work** — only for local preview (see above), which RStudio already handles internally.

**One-time setup, on GitHub.com (not in RStudio):**

1. Push this repository to GitHub (see "Day-to-day workflow" below for the git commands).
2. On the repository's GitHub page, go to **Settings → Pages**.
3. Under "Build and deployment" → "Source," select **"GitHub Actions"** (not "Deploy from a branch").
4. That's it. The workflow will run automatically on your next push.

**Every time after that**, publishing an update is automatic: just push your changes to the `main` branch (see below), and GitHub renders and republishes the site for you within a minute or two. You can watch its progress under the repository's **Actions** tab.

## Day-to-day workflow

1. Edit `.qmd` files in RStudio.
2. Click **Render** (or **Preview**) to check your changes locally.
3. Commit and push using RStudio's **Git** tab (or `git add`, `git commit`, `git push` in the Terminal).
4. That's it — pushing to `main` automatically triggers the GitHub Actions workflow, which renders and updates the live site within a minute or two. No `quarto publish` command needed, on this machine or any other.

::: {.callout-tip}
If you want to double check a build succeeded (or see why one failed), go to the repository's **Actions** tab on GitHub — each push shows up as a workflow run, with full logs.
:::

## Releasing solutions after a session

The solution zips live in `downloads/` but are not linked on the site until you switch them on.
In `_quarto.yml`, change e.g. `solutions2: false` to `solutions2: true`, commit, push and run the workflow.
The "Solutions" list on the Templates & Materials page (`materials.qmd`) then shows the download link.
Note: the zips are in the repository either way, so anyone who can open a public repo can see them.
To keep them completely private until release, keep the zip on your computer and add it to `downloads/` on release day.
