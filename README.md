# DraftKings — Interactive Cost of Capital

A cost-of-capital analysis you can move. Every input of the WACC calculation is a live slider, and the whole model, the sensitivity tables, the comparable-company betas and a 3D WACC surface, recomputes as you drag.

**Live demo:** `https://draftkings-coc.vercel.app/`

---

## Overview

A standard cost-of-capital write-up hides its own fragility: it reports one number and buries the assumptions that produced it in an appendix. This project inverts that. The six inputs that drive DraftKings' WACC are exposed as controls, and the result updates instantly, so the interesting question stops being *what is the WACC* and becomes *how much does the answer depend on what we assumed*.

Base case: **WACC 8.00%**, on an all-equity capital structure, from a risk-free rate of 0.90%, a market risk premium of 5.00% and an asset beta of 1.4186 unlevered from eight listed gaming comparables.

## Screenshots

`[add 2–3 screenshots: the parameter panel with the live WACC, the 3D surface, and one sensitivity grid]`

## How it works

**1. Model parameters.** Six sliders, each bounded to a defensible range: risk-free rate (0.30–3.00%), market risk premium (3.0–7.0%), asset beta (0.80–2.00), debt weight (0–60%), cost of debt (1.0–8.0%), tax rate (0–35%).

**2. The calculation.** Standard CAPM and WACC, relevered at the chosen capital structure:

- Equity beta, relevered without a tax shield: `βe = βa ÷ E/(D+E)`, equivalently `βe = βa × (1 + D/E)`
- Cost of equity: `Re = Rf + βe × MRP`
- After-tax cost of debt: `Rd × (1 − t)`
- `WACC = E/(D+E) × Re + D/(D+E) × Rd × (1 − t)`

**3. Comparable companies.** Asset betas unlevered from eight listed gaming and casino operators, Las Vegas Sands, MGM Resorts, Caesars, Penn Entertainment, Wynn Resorts, Churchill Downs, Boyd Gaming and Monarch, each with its own equity beta and leverage. Their mean asset beta, 1.4186, rounded to 1.42, is the base-case input.

**4. Sensitivity.** Two grids, WACC against Rf × MRP and against βa × MRP, plus a 3D surface rendered with three.js that can be rotated and zoomed, with three axis pairings and a marker on the base case. The surface is the argument the tables can only imply: the answer is a slope, not a point.

**5. Waterfall.** A bridge from the risk-free rate to the final WACC, showing what each component contributes.

## Tech stack

- **Rendering:** a single self-contained HTML file, ~28 KB, no framework and no build step
- **3D:** three.js (r128) for the interactive WACC surface
- **Everything else:** vanilla JavaScript and CSS
- **Deployment:** Vercel

## Getting started

There is nothing to install. Open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000
```

Then open [http://localhost:8000](http://localhost:8000). The only external dependency is the three.js CDN script, so the page needs a network connection the first time.

## Team

Giulia Moroni, co-founder — https://www.linkedin.com/in/giuliamoroni/

Coursework for Corporate Finance, Bocconi University, 2026.

*Academic coursework. Not affiliated with or endorsed by DraftKings Inc.; the company is used as an analysis subject only, and none of the figures here are investment advice.*
