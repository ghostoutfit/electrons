# electrons — Electrons Digital Model

Standalone single-file sim deployed to `ghostoutfit.github.io/electrons/`.
Vanilla HTML + CSS + JS only. No build step — edit `index.html` directly.

To run locally: `python3 -m http.server 8099 --directory /Users/jkremer/Projects/electrons`, then open `localhost:8099/`.

## Versions

| Path | URL | Description |
|------|-----|-------------|
| `v1/index.html` | `/v1/` | Primary sim — shells, trails, orbit3d tabs; force visualization panel (Force on Shell / Force on Electron modes); Show Forces button |
| `v5/index.html` | `/v5/` | Extends v1 with wire-grab mode; electrons can be dragged via an interactive wire |
| `v7/index.html` | `/v7/` | Alternate build (details TBD) |
| `index.html` (root) | `/` | Homepage — nav cards linking to v1, v5, v7 |

**Active development targets: v1 and v5.** Changes to UI layout, force viz, or physics should be applied to both.

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

## Key JS architecture (v1 / v5)

- **`idleParticleLoop()`** — main animation loop; any exception before it starts (at init) freezes the page
- **`syncTabButtons()`** — called at init; references `forceCtrlBox` (not `forceModeRow`)
- **`syncForceVizVisibility()`** — gates force panel and Force Values checkbox to shells tab; hides Force Values when `arrowMode === 0`
- **`drawForceVizShell()`** — force panel, shell mode; repulsion arrows always draw radially outward (`cosA, sinA`) regardless of inner-electron clamped positions
- **`getShellRadius(s)`** — shell 0 clamped to `Math.max(px, animParent.sphereR * 1.4)` for heavy atoms; this is why inner-shell electrons appear close to outer shells visually, but force arrows are normalized to outward

## Shell colors

```js
SHELL_COLORS = ['#ff4488', '#00ddff', '#ff8800', '#88ff00']
// index:          0 (pink)   1 (blue)   2 (orange)  3 (lime)
```
