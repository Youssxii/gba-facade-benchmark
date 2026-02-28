# GBA-Facade: Benchmarking the GlobalBuildingAtlas for Autonomous Facade Maintenance at Planetary Scale

**Paper**: [GBA-Facade-Benchmark.pdf](main.pdf)

## Abstract

We present GBA-Facade, the first large-scale benchmark evaluating the [GlobalBuildingAtlas](https://github.com/zhu-xlab/GlobalBuildingAtlas) (2.75B buildings) for autonomous facade maintenance planning. We ingest the complete dataset into PostgreSQL (837 GB) and perform:

1. **Data quality audit**: 65.9M buildings (2.38%) with negative height artifacts identified and corrected
2. **Facade area estimation**: 4.18B m² across 408,812 buildings above 50m worldwide
3. **Spatial query benchmarks**: Sub-2-second city-scale lookups using tile-based B-tree indexing
4. **Validation**: Cross-reference against NYC PLUTO (height MAE 3.12m, R²=0.84)

## Key Results

| Metric | Value |
|--------|-------|
| Total buildings ingested | ~2.75B |
| Buildings with valid height | ~2.71B |
| Negative heights corrected | 65,916,707 (2.38%) |
| Buildings >50m globally | 408,812 |
| Total facade area (>50m) | 4.18B m² |
| Mean building height | 3.48m |
| Max building height | 237.31m |
| Database size | 837 GB |
| Query latency (city-scale) | <2 seconds |

## Infrastructure

- **Instance**: AWS r7g.2xlarge (8 vCPU Graviton3, 64 GB RAM)
- **Storage**: 984 GB NVMe EBS
- **Database**: PostgreSQL 16, hash-partitioned (16 partitions)
- **Index**: B-tree on `tile` column (no PostGIS GIST needed)

## Dataset

This benchmark uses the [GlobalBuildingAtlas](https://mediatum.ub.tum.de/1782307) by Zhu et al. (2025), published in Earth System Science Data.

```bibtex
@Article{essd-17-6647-2025,
  AUTHOR = {Zhu, X. X. and Chen, S. and Zhang, F. and Shi, Y. and Wang, Y.},
  TITLE = {GlobalBuildingAtlas: an open global and complete dataset of building polygons, heights and LoD1 3D models},
  JOURNAL = {Earth System Science Data},
  VOLUME = {17},
  YEAR = {2025},
  PAGES = {6647--6668},
  DOI = {10.5194/essd-17-6647-2025}
}
```

## Citation

```bibtex
@article{chretien2026gba-facade,
  title={GBA-Facade: Benchmarking the GlobalBuildingAtlas for Autonomous Facade Maintenance at Planetary Scale},
  author={Chretien, Enguerand and Jouanno, Theophile and Winckler, Jean-Philippe},
  year={2026},
  note={Preprint}
}
```

## DOI

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.18812079.svg)](https://doi.org/10.5281/zenodo.18812079)

## License

MIT

## About VitroBOT

[VitroBOT](https://vitrobot.site) develops autonomous facade cleaning robots. SIREN: 993 728 914.
