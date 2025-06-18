# Data Driven Modelling of Cell Differentiation Trajectories 

A reproducible analysis pipeline to:

1. **Annotate** intestinal epithelial cell clusters (stem, TA, goblet, enteroendocrine, etc.)
2. **Visualize** clean, publication-quality UMAPs with on-plot labels
3. **Infer** cell–cell communication networks using NATMI (and LIANA)
4. **Summarize** interactions in heatmaps and tables

---

## 📁 Repository Structure

```
gut-cell-comm/
├── data/
│   ├── raw/                 # Raw input files (FASTQ, count matrices)
│   └── processed/           # Processed AnnData objects, QC’d matrices
│
├── notebooks/
│   ├── 01_preprocessing.ipynb
│   ├── 02_umap_labeling.ipynb
│   └── 03_cellcell_heatmap.ipynb
│
├── scripts/
│   ├── annotate_clusters.py  # Annotation helper functions
│   ├── plot_umap.py          # Clean UMAP plotting utilities
│   └── build_heatmap.py      # NATMI / LIANA wrapper script
│
├── results/
│   ├── figures/             # Exported UMAPs & heatmaps (PNG, PDF)
│   └── tables/              # CSV/TSV outputs of marker genes & interactions
│
├── environment.yml          # Conda environment specification
├── requirements.txt         # Pip dependencies
├── LICENSE                  # MIT License
└── README.md                # This file
```

---

## 🚀 Quickstart

1. **Clone the repo**

   ```bash
   git clone https://github.com/yourusername/gut-cell-comm.git
   cd gut-cell-comm
   ```

2. **Set up the environment**

   ```bash
   conda env create -f environment.yml
   conda activate gut-cell-comm
   # or: pip install -r requirements.txt
   ```

3. **Run the notebooks**
   Launch JupyterLab:

   ```bash
   jupyter lab notebooks/
   ```

   * `01_preprocessing.ipynb`: QC, normalization, HVG selection
   * `02_umap_labeling.ipynb`: clustering, annotation, clean UMAP plotting
   * `03_cellcell_heatmap.ipynb`: NATMI/LIANA analysis and heatmaps

4. **Or execute the scripts**

   ```bash
   python scripts/annotate_clusters.py \
       --adata data/processed/my_adata.h5ad \
       --out results/tables/cluster_annotations.csv

   python scripts/plot_umap.py \
       --adata data/processed/my_adata.h5ad \
       --labels results/tables/cluster_annotations.csv \
       --out results/figures/umap_clean.png

   python scripts/build_heatmap.py \
       --adata data/processed/my_adata.h5ad \
       --method natmi \
       --out results/figures/heatmap_natmi.png
   ```

---

## 📊 Results

* **Publication-ready UMAPs** with on-plot labels
* **NATMI & LIANA heatmaps** summarizing cluster interactions
* **Tables** of top ligand–receptor pairs per sender–receiver pair

All outputs are in `results/figures/` and `results/tables/`.

---

## 🛠️ Workflow Details

* **Data input**: raw counts → AnnData (`.h5ad`) with `.obs['refined_type']`
* **Preprocessing**: filtering, normalization, highly-variable gene (HVG) selection, PCA, neighbor graph, UMAP
* **Annotation**: marker-gene–based cluster labeling + manual curation
* **Visualization**: clean UMAPs using `matplotlib` and `scanpy`, with semi-transparent dots and haloed text labels
* **Interaction inference**:

  * **NATMI**: `create_communication_network` for ligand–receptor scoring
  * **LIANA**: `rank_aggregate` for consensus scoring across multiple resources
* **Summarization**: pivot interaction scores into sender×receiver matrices and plot heatmaps

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feat-xyz`)
3. Implement your changes and add tests if applicable
4. Submit a pull request

Please follow the existing code style and add clear documentation for new features.

---

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
