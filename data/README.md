# Data requirements

The source imagery is not distributed with this repository. The notebooks expect a data directory containing paired imagery and vector inputs for the Lokoué, Dzanga and Mbeli study sites.

## Expected structure

For each site, the following files are required:

```text
DATA_ROOT/
├── lokoue/
│   ├── lokoue_RGB.TIF
│   ├── lokoue_NED.TIF
│   ├── mask_lokoue.gpkg
│   ├── lokoue_aoi_tall.gpkg
│   ├── lokoue_aoi_mid.gpkg
│   ├── lokoue_aoi_small.gpkg
│   ├── crowns_lokoue_tall.gpkg
│   ├── crowns_lokoue_mid.gpkg
│   └── crowns_lokoue_small.gpkg
├── dzanga/
│   └── corresponding Dzanga files
└── mbeli/
    └── corresponding Mbeli files
```

The internal labels `tall`, `mid` and `small` correspond respectively to the high-, intermediate- and low-canopy strata reported in the dissertation.

## Satellite imagery

Each site requires two spatially aligned Pléiades Neo products:

* `*_RGB.TIF`: red, green and blue bands;
* `*_NED.TIF`: near-infrared, red-edge and deep-blue bands.

The imagery was supplied by the Zoological Society of London under licence and cannot be redistributed. The notebooks verify raster alignment, resolution, extent, coordinate reference system and datatype before processing.

## Vector inputs

The vector inputs comprise:

* nine manually delineated crown datasets;
* nine area-of-interest boundaries; and
* three boundary-crown exclusion masks.

These files contain polygon geometries but no satellite spectral values. They are being prepared for deposition in a suitable research-data repository and will be linked from the main README when a permanent identifier is available.

## Canopy-height model

The canopy-height model described by Tolan et al. (2024) was used only to guide the selection of canopy strata. It was not supplied to Detectree2, used during training or included in model evaluation.

## Generated files

The notebooks create temporary stacks, crops, tiles and keep-region files in the Colab runtime. Model checkpoints, candidate-prediction caches and other generated geospatial files are excluded from version control.
