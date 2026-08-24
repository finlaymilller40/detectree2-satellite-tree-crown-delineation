# Evaluating Detectree2 for Tree Crown Delineation from Multispectral Satellite Imagery in the Congo Basin

This repository contains the analysis code supporting an MSc Ecology and Data Science research project conducted at University College London in collaboration with the Zoological Society of London.

## Overview

Individual-tree crown delineation remains challenging in dense tropical forests, particularly from satellite imagery rather than centimetre-scale airborne imagery. This study evaluated whether Detectree2 could be adapted to 0.3 m Pléiades Neo imagery from three Congo Basin forest sites and whether near-infrared, red-edge and deep-blue bands improved delineation beyond matched RGB inputs.

A total of 1,027 crowns were annotated across nine areas of interest at Lokoué, Dzanga and Mbeli. Three-fold leave-one-site-out evaluation ensured that each test site was excluded from model development.

Two hypotheses were evaluated:

1. Regional fine-tuning improves performance relative to the pretrained Detectree2 RGB model.
2. Six-band multispectral imagery improves performance relative to a preprocessing-matched three-band model.

## Repository structure

The notebooks should be read and run in numerical order:

* `01_h1_training.ipynb`: RGB preprocessing and leave-one-site-out fine-tuning.
* `02_h1_evaluation.ipynb`: comparison of pretrained and fine-tuned RGB models.
* `03_h2_training.ipynb`: matched three-band and six-band multispectral training.
* `04_h2_evaluation.ipynb`: H2 evaluation, result verification and figure generation.

## Analytical design

For H1, the original pretrained RGB model was compared with models fine-tuned using two development sites and evaluated on the third. For H2, matched three-band and six-band models were constructed from the same multispectral tiles and trained through the same multispectral pathway.

Predictions were reconstructed in geographic coordinates and deduplicated using score-ordered non-maximum suppression. Confidence and NMS thresholds were selected using validation areas and applied unchanged to the corresponding held-out site. Predictions were matched one-to-one with reference crowns at an intersection-over-union threshold of 0.5.

## Main results

Regional fine-tuning increased macro-averaged F1 from 0.237 to 0.442, with improvement at all three held-out sites.

Adding near-infrared, red-edge and deep-blue bands produced little overall change. Macro-averaged F1 was 0.439 for the matched three-band model and 0.447 for the six-band model, with small gains at two sites and a decrease at the third.

## Computational environment

The notebooks are designed for Google Colab with a GPU accelerator. Detectron2 and Detectree2 are installed from pinned Git revisions:

* Detectron2: `a2f4a8771ab77e8411c26b27f24f9489a28a2453`
* Detectree2: `d9fb07f0dfb493f34def563c1ff896fecd59210d`

The data-root variables near the beginning of each notebook must be updated if the input files are stored outside the documented Google Drive structure.

## Data availability

The Pléiades Neo imagery was supplied by the Zoological Society of London under licence and cannot be redistributed through this repository.

The canopy-height model described by Tolan et al. (2024) was used only to guide sampling and was not provided to Detectree2 or used during evaluation.

Crown annotations, area-of-interest boundaries and boundary masks contain no satellite spectral information and are being prepared for deposition in a suitable research-data repository. A permanent link will be added following deposition.

Model checkpoints, tiled imagery and intermediate prediction caches are not included because of their size and the restrictions associated with the source imagery.

## Acknowledgements

This research was conducted with support from the Zoological Society of London and University College London.
