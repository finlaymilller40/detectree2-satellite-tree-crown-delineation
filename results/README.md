# Results

The evaluation notebooks reproduce the performance summaries reported in the dissertation and verify them against expected values using explicit assertions.

Generated outputs are written to Google Drive rather than directly to this repository.

## H1 outputs

`02_h1_evaluation.ipynb` produces:

* `dataset_composition.csv`: valid area, crown abundance, crown density, median crown area and annotated coverage by site and canopy stratum;
* `h1_site_results.csv`: pretrained and fine-tuned precision, recall and F1 by held-out site and as macro-averages;
* `h1_stratum_results.csv`: fine-tuned performance by site and canopy stratum;
* `h1_threshold_selection.csv`: validation-selected confidence and NMS thresholds;
* `results_h1_rgb.json`: machine-readable H1 protocol and results; and
* `H1_dzanga_figure_layers.gpkg`: reference and classified prediction layers used to construct the spatial evaluation figure.

## H2 outputs

`04_h2_evaluation.ipynb` produces:

* `h2_site_results.csv`: matched three-band and six-band precision, recall and F1;
* `h2_stratum_results.csv`: performance by site and canopy stratum;
* `h2_threshold_selection.csv`: validation-selected confidence and NMS thresholds;
* `h2_model_audit.csv`: checkpoint and available-configuration checks;
* `results_h2_ms.json`: machine-readable H2 protocol and results;
* `table_4_combined.csv`: combined dataset and performance summary;
* `figure_4_macro_performance.png`: macro-averaged model comparison; and
* `figure_5_stratum_performance.png`: performance across sites and canopy strata.

## Reported headline results

| Comparison                        | Macro F1 |
| --------------------------------- | -------: |
| Pretrained RGB                    |    0.237 |
| Fine-tuned RGB, H1 pathway        |    0.442 |
| Fine-tuned three-band, H2 pathway |    0.439 |
| Fine-tuned six-band               |    0.447 |

Regional fine-tuning produced the principal improvement. Adding near-infrared, red-edge and deep-blue bands produced a macro-F1 increase of 0.008 relative to the matched three-band model, but the direction of change varied among sites.

## Repository policy

Small non-spatial result tables and final figures may be added to this directory following final verification. Model checkpoints, tiled imagery, spatial prediction caches and other large or restricted derived files are excluded from version control.
