# Hydropower RAI Workforce Data

This repository contains the publication data package created by National Laboratory of the Rockies (NLR) for the hydropower Robotics-and-AI workforce study.

## At A Glance

```text
.
├── CITATION.cff
├── data/
│   ├── CHECKSUMS.sha256
│   ├── DATA_DICTIONARY_all.md
│   ├── hydropower_rai_matches_full.csv
│   └── README.md
├── LICENSE
└── README.md
```

## Files

- `data/hydropower_rai_matches_full.csv`: main publication dataset.
- `data/DATA_DICTIONARY_all.md`: field definitions, codes, units, and missing-value notes.
- `data/CHECKSUMS.sha256`: file integrity manifest for the publication package.
- `data/README.md`: quick index of the data folder.
- `CITATION.cff`: machine-readable citation metadata for GitHub and indexers.

To verify the archive after download, compare file hashes against `data/CHECKSUMS.sha256`.

## What The Data Contains

Each row in the CSV is one task-to-technology match in the hydropower RAI workforce analysis. The table includes task text, O\*NET occupation mappings, RAI technology classifications, performer/supporter roles, automation exposure, and provenance fields.

For the full column-level definitions, see [data/DATA_DICTIONARY_all.md](data/DATA_DICTIONARY_all.md).

## License

The data in this repository are licensed under the Creative Commons Attribution 4.0 International License. See [LICENSE](LICENSE).
