# COVID-19 meta-analysis, Aronow Lab

## Project details

Last updated: Thu Jan 28 12:12:42 2021

Author: Pablo Garcia-Nieto

Project title: not available yet (Meta analysis of COVID datasets, Bruce Aronow's lab)

DOI: not available yet

Reqs:

- scanpy
- cellxgene with schema functions

Note:
- Most of the curation was done by Kang, a grad student in the Aronow lab
- There was a lot of back-and-forth with Kang, and after many iterations he was able to incorporate our schema into the data. I still had to correct some typos in ceartain categories, to append labels associated with ontology terms, and to correct embeddings for one file.
- There is a total of 10 datasets:
    - 5 individual datasets from other publications
    - 1 meta analysis integrating all 4 datasets
    - 4 meta analysis datasets contain a specific cell types with subcluster information
- A note from Kang about embeddings from individual studies:
    *Among those 5 datasets, Schulte-Schrepping et al. and Wilk et al. provided both cell type annotations and UMAP coordinates. We kept their original information in the h5ad files. Besides, we also added our reannotated cell designations. For the rest datasets which didn’t provide cell annotations or UMAP coordinates, we used our own annotations and UMAP coordinates.*

## Curation steps

Clone this repo and execute the steps below from the downladed path

- Download data. Get the following files from this dropbox [folder](https://www.dropbox.com/sh/uv3f1w43rb62mb7/AACROayDUXtjaWuUUCwodiQqa) and store them in `./data/original/`

    - B_cell_subcluster.h5ad
    - COVID-19_PBMC_Arunachalam_et_al.h5ad
    - COVID-19_PBMC_Guo_et_al.h5ad
    - COVID-19_PBMC_Lee_et_al.h5ad
    - COVID-19_PBMC_Schulte-Schrepping_et_al.h5ad
    - COVID-19_PBMC_Wilk_et_al.h5ad
    - PBMC_merged_normalized_addRaw_coordinatesFixed_0126.h5ad
    - T_NK_Subcluster_0121.h5ad
    - monocyte_subcluster_0126.h5ad
    - platelets_subcluster.h5ad

- Correct mistakes, append labels to ontolgies, ammend embeddings. Data will be saved to `./data/remixed/`

```bash
# For the meta analysis integrated data
python3 scripts/add_labels.py
# For the rest
python3 scripts/add_labels_general.py ./data/original/ ./data/remixed/
```
- Validate schema


```bash
bash ./scripts/validate_all.sh
```
