# neuro-disease-ml-pipeline

Testing whether disease-associated genes are enriched in the brain regions they clinically destroy — using GWAS Catalog + Allen Human Brain Atlas.

---

## The Question

Neurodegenerative diseases don't attack the brain randomly.

- **Parkinson's** — selectively kills the *substantia nigra*
- **Huntington's** — targets the *striatum*
- **Alzheimer's** — begins in the *hippocampus and cortex*

Nobody has a clean mechanistic answer for *why that region and not another*.

**Hypothesis:** regional selective vulnerability might be explained by regional gene expression — a region degenerates because the disease's risk genes happen to be especially active in that specific patch of brain tissue.

This project tests that hypothesis computationally.

---

## Approach

| Step | What happens |
|------|--------------|
| 1. Get risk genes | Pull genome-wide significant SNP-trait associations from the GWAS Catalog |
| 2. Get expression data | Pull spatial gene expression per brain region from the Allen Human Brain Atlas |
| 3. Score regions | Aggregate expression score for the disease gene set, per region |
| 4. Test significance | Permutation test vs. random gene sets |
| 5. Visualize | Plot enrichment scores on a 3D brain mesh |
| 6. Validate | Check predicted regions against known disease pathology |
| 7. Scale | Repeat across diseases, measure hit-rate |

This is a ranking/regression problem wrapped in a hypothesis test — not classification. The core output per region is a continuous score, not a class label.

---

## Data Sources

- **[GWAS Catalog](https://www.ebi.ac.uk/gwas/)** — curated GWAS associations, queried via REST API
- **[Allen Human Brain Atlas](https://human.brain-map.org/)** — regional gene expression, accessed via [`abagen`](https://github.com/rmarkello/abagen)

---

## Repo Structure