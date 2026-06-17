# electrons — Electrons Digital Model

Standalone single-file sim deployed to `ghostoutfit.github.io/electrons/`.
Vanilla HTML + CSS + JS only. No build step — edit `index.html` directly.

To run locally: `python3 -m http.server` in this directory, then open `localhost:8000/`.

## Images

```
images/
  favicon.png / favicon.svg
  logo-placeholder.png
```

## Deployment

GitHub Pages from `main` branch root (via GitHub Actions). Push to `origin` to deploy.
Remote: `https://github.com/ghostoutfit/electrons.git`

A `mobile-test` branch deploys to `/test/` subdirectory via the same workflow.
