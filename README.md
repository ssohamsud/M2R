# Data-Driven Modelling of Intestinal Cell Differentiation Trajectories 🍃🔬

**Project Aim:** Combine single-cell RNA-seq analysis, trajectory inference, and cell–cell communication to map how intestinal stem cells diversify into absorptive and secretory lineages and identify key intercellular signaling pathways.

**Authors:** Soham Sud, Yifan, Sahil Rai, Michael Li, Ben Thimbleby
**Supervisor:** Omer Karin

---

## 🚀 Quickstart

```bash
# Clone and enter project folder
git clone https://github.com/yourusername/M2R_Group_19_Intestine.git
cd M2R_Group_19_Intestine

# Install environment
conda env create -f environment.yml
conda activate M2R
# or: pip install -r requirements.txt

# Run analyses interactively with JupyterLab
jupyter lab notebooks/
# Or execute scripts end‑to‑end:
python scripts/preprocess.py --input data/raw/counts.csv --output data/processed/adata.h5ad
python scripts/cluster_and_annotate.py --adata data/processed/adata.h5ad
python scripts/run_trajectories.py --adata data/processed/adata.h5ad
python scripts/build_interactions.py --adata data/processed/adata.h5ad
```

---

## 📊 Key Results

* **Cluster annotation:** Identified ISC, TA progenitors, enterocytes, goblet, Paneth, tuft, and enteroendocrine cells.
* **Trajectories:** Secretory (Paneth/Goblet/Enteroendocrine) vs. absorptive (Enterocyte) branching mapped by DPT, CellRank, and Palantir.
* **Cell–cell signaling:** Highlighted Paneth→ISC niche factors (Wnt3, EGF, DLL4) and enteroendocrine hormone signals.

Results are saved in `results/figures/` (plots) and `results/tables/` (tables).

---

## 🧬 Methods Overview

1. **Preprocessing:** Filtering, log-normalization, HVG selection, PCA, neighbor graph, UMAP (Scanpy).
2. **Clustering & Annotation:** Leiden clustering + marker-gene–based assignment.
3. **Trajectory Inference:** DPT pseudotime, CellRank fate mapping, Palantir random-walk pseudotime.
4. **Communication Analysis:** LIANA rank-aggregate (mouse consensus) and NATMI `create_communication_network`; aggregated into sender→receiver heatmaps.

---

## 🤝 Contributing

1. Fork the repo
2. Create a branch (`git checkout -b feat-xyz`)
3. Implement changes & add tests
4. Submit a pull request

Please follow existing code style and update docs accordingly.

---

## 📄 License

MIT © Imperial College London
