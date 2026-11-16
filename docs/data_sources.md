# Data sources

The workflow uses HDD metadata to map compounds across four feature sources:

| Source | ORCESTRA release | ORCESTRA `versionInfo.version` | Record | Role |
| --- | --- | --- | --- | --- |
| HDD | `HDD_v3` | `3` | [22133259](https://zenodo.org/records/22133259) | Compound mappings, ATC codes, and MOA labels |
| GEOM | `HDD_v2_GEOM` | `1` | [20019577](https://zenodo.org/records/20019577) | Molecular descriptors from `WHIM_hp.parquet` |
| LINCS | `HDD_v2_LINCS` | `1` | [20019530](https://zenodo.org/records/20019530) | Expression signatures from `signatures.parquet` |
| JUMP | `HDD_v2_cpg0016-jump` | `2` | [20028579](https://zenodo.org/records/20028579) | Cell-morphology features from `cpcnn.parquet`, with sample metadata |
| NCI60 | `NCI60_2026` | `2026` | [21043047](https://zenodo.org/records/21043047) | PharmacoSet response features summarized using `aac_recomputed` |

Release names and version fields are from the public ORCESTRA
[annotations API](https://orcestra.ca/api/annotations/available) and
[PharmacoSet API](https://orcestra.ca/api/pset/available).

Download URLs and the NCI60 screen identifier are configured in
[`config/downloads.yaml`](https://github.com/bhklab/fused-embedding-pipeline/blob/main/config/downloads.yaml).
Supply a compatible YAML file through the applet's `downloads` input to override
those settings. The default sources must be reachable from DNAnexus workers.

To reuse data, provide `raw_data` and/or `viability` using the layout described in
the [user guide](https://github.com/bhklab/fused-embedding-pipeline#reuse-inputs-or-change-model-settings).
Custom files must retain the schemas expected by the preprocessing scripts;
changing a URL alone does not adapt a different dataset schema.

Embedding coverage depends on compound overlap among the feature sources and
eligibility filters. Record the source configuration and input file identities
with an analysis when comparing results or sharing derived embeddings.
