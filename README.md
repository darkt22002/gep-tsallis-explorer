# GEP Tsallis q-Sweep Explorer

**Interactive dashboard for visualizing entropy dynamics across Tsallis q-indices in billion-digit mathematical constants.**

![LCARS Dashboard](screenshot.png)

## Overview

This dashboard provides real-time interactive exploration of the Guided Entropy Principle (GEP) applied to 11 mathematical constants (π, e, φ, √2, √3, ln2, Fibonacci, Catalan, Euler-Mascheroni γ, Lemniscate ϖ, Gauss G) computed at 1 billion digits each across multiple Tsallis entropy indices.

The core equation:

```
dS = ‖∇S_q‖   (Tsallis entropy gradient, q=1.0 → Shannon)
```

Where `q < 1.0` amplifies rare digit events (super-additive regime) and `q > 1.0` amplifies common events (sub-additive regime).

## Features

- **q-Index Slider** — Sweep through Tsallis q values and watch all metrics update in real-time
- **Scale Slider** — Explore entropy dynamics across window sizes from 25 to 50,000 digits
- **Constant Selection** — Toggle individual constants on/off for targeted comparison
- **Kurtosis Waterfall** — κ(∇S_q) convergence patterns across all scales
- **Tabbed Detail Panels:**
  - **Helix** — Winding numbers and interleave pair structures (CROSSING / MODULATED detection)
  - **Distribution** — Skew vs kurtosis scatter and per-constant kurtosis bars
  - **Recall** — Pattern recurrence heatmap across pattern lengths 2-6
  - **KS Significance** — Kolmogorov-Smirnov test matrix (scale × constant)
  - **Entropy** — Mean entropy curves across scales

## Usage

### Self-Contained (Embedded Data)

The `gep_q_dashboard.html` file includes embedded data and can be opened directly in any browser:

```
Open gep_q_dashboard.html in Firefox/Chrome
```

No server required. No dependencies. Single file.

### With External Data

For updated data, the dashboard can also load from an external JSON file (`gep_q_dashboard_data.json`) placed in the same directory. The embedded data takes priority if present.

## Data Pipeline

The dashboard visualizes results from the GEP analysis pipeline:

1. **y-cruncher** — Computes mathematical constants to 1 billion digits
2. **GEP v4 Tsallis Engine** — Multiscale entropy analysis at each q-index
3. **Recall GPU** — CUDA-accelerated pattern recurrence scoring
4. **Helix Mapper** — Cross-constant interleave and winding analysis
5. **Data Extractor** → `gep_q_dashboard_data.json`
6. **This Dashboard** → Interactive visualization

## Technical Details

- Pure HTML/CSS/JS — no frameworks, no build step
- Canvas-based rendering for performance
- LCARS-inspired interface theme
- Responsive layout with tabbed navigation
- Handles 7+ q-values × 11 constants × 10 scales seamlessly

## Research Context

The GEP framework discovers that mathematical constants exhibit universal kurtosis convergence patterns under entropy gradient analysis. The Tsallis q-sweep extends this by probing how the entropy kernel's sensitivity to rare vs. common digit events affects the observed structure.

Key findings visible in the dashboard:
- **Winding number shift** — Helix winding changes measurably across q values
- **φ × √2 phase-locking** — At q=1.5, this pair transitions from CROSSING to MODULATED structure
- **Universal NONE signal** — No constant shows statistically significant departure from randomness at any q tested

## Author

**Gary W. Floyd**
Lumiea Systems Research Division / ThunderStruck Service LLC

- GEP Framework: [Academia.edu](https://www.academia.edu)
- Hardware: Dell R810 (40 cores, 300GB ECC) + HP DL380p (K80 GPUs)

## License

MIT License — See [LICENSE](LICENSE) for details.

The visualization tool is open source. The underlying analysis scripts, mathematical frameworks, and research data remain proprietary to Lumiea Systems Research Division / ThunderStruck Service LLC.
