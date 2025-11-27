# 🐦 Birds Behaviour Analysis from Bounding-Box Annotations

This project demonstrates how meaningful behavioural information can be extracted from a wildlife feeder dataset **using only COCO-style bounding box annotations** — without pose estimation, individual identity tracking, or temporal modelling.

From static frames alone, the pipeline quantifies:

- **Species co-occurrence** — who feeds together
- **Social spacing** — how close individuals stay to one another
- **Spatial occupancy** — preferred locations around the feeder
- **Co-feeding social network** — tolerance and associations between species
- **Dominance proxy** — centrality in crowded scenes as a measure of access to the food source

This project aims to repurpose standard object detection datasets for **computational ethology**, showing that even minimal annotations can reveal interpretable behavioural structure.

---

##  Dataset
- Format: **COCO JSON**
- Each annotation includes: `image_id`, `category_id`, `bbox [x, y, width, height]`
- Species label derived from `category_id`
- Images contain **multiple bird species at a feeder**

>  **Pose estimation, identity tracking, and video trajectories were not used.**  
> The analysis intentionally relies only on bounding boxes.

---

## Methods Overview

| Metric | Technique | Output |
|--------|-----------|--------|
| Co-occurrence | Count species pairs per frame | Heatmap |
| Social spacing | Pairwise Euclidean centroid distances | Boxplot |
| Spatial occupancy | 2D centroid histogram per species | Heatmap per species |
| Social network | Weighted graph from co-occurrence | Spring layout |
| Dominance proxy | Distance from group centroid in crowded scenes | Bar chart |

All computations are based on **normalized centroid coordinates** extracted from bounding boxes.

---

##  Repository Structure

     Birds_Behaviour_Analysis/
      │── results/                                # Output visualizations
      │ ├── cooccurrence_heatmap.png
      │ ├── social_spacing_boxplot.png
      │ ├── social_network_graph.png
      │ ├── dominance_barplot.png
      │ └── occupancy_<species>.png
      |── Analysis.ipynb                          # Main pipeline
      │── Birds_Behaviour_Analysis_Report.pdf     # Full written analysis
      │── README.md
      └── _annotations.coco.json                  # COCO annotation file (not included here if confidential)




---

## Output Visualizations

- **Co-occurrence heatmap**
- **Species-pair distance distributions (boxplot)**
- **Spatial occupancy heatmaps (per species)**
- **Co-feeding social network graph**
- **Dominance score (centrality-based bar chart)**

Each can be directly used in research reports or presentations.

---

## Technologies Used
- Python 3
- NumPy, Pandas
- Matplotlib
- SciPy
- NetworkX
- PIL

---

##  Motivation and Next Steps

This project serves as a lightweight behavioural analysis baseline for wildlife datasets that **lack pose estimation or ID tracking**.

Future extensions (planned):
- Multi-animal pose estimation (DeepLabCut / SuperAnimal)
- Identity-aware tracking and displacement events
- Behavioural state classification from pose dynamics
- Temporal interaction graphs
