# Smart-SH-Emergency-AI-based-pluvial-flood-modelling-for-operational-forecasts-in-Schleswig-Holstein

AI based flood-depth prediction for pluvial flood scenarios for Schleswig-Holstein, using geospatial raster data, hydrodynamic simulation outputs (GRASS/SIMWE) and U-net like convolutional neural networks with calibration and spatial evaluation.

This Repository contains the complete analysis workflow for investigating AI-supported flood prediction within the Project: Smart SH Emergency. The workflow focuses on the preparation of geospatial training data, deep-learning-based flood-depth modelling, transfer to a second Region of Interest and the post-processing and evaluation of the predicted flooding against a hydrodynamic reference simulation.

This study is part of the course:
zertifikatstudium GeoDataScience
gds050-01a: Ausgewählte Aspekte des Geoinformationswesens (S), WiSe 25/26
Topic: Smart SH Emergency

Author: Justin Lingg-Laham
09.03.2026

# Project Overview

The aim of this study was to investigate wether a U-Net-like convolutional neural network can learn flood-depth patterns from hydrodynamic simulation data and transfer this knowledge to a second rural study area. The Model was trained on raster patches derived from a urban study area and then transfered to an rural study area in order to assess its ability to reproduce spatial flood characteristics under synthetic heavy-rainfall conditions.
In addition to the raw model prediction, post-hoc calibration methods were used to improve statistical agreement between predicted and reference flood depths (Quantile Mapping). The workflow therefore addresses both the learning of physically informed flood patterns and the practical usability of AI-generated flood maps for emergency-related geospatial analysis.

# Methods
The workflow consists of 3 main components:

## Part 1: Data preparation and patch extraction
1.1 Load and harmonize geospatial raster inputs
1.2 Prepare multi-channel model input data (e.g. DEM, precipitation, Manning roughness coefficient, infiltration)
1.3 Load hydrodynamic reference water-depth rasters
1.4 Extract fixed-size raster patches for supervised learning
1.5 Balance wet and dry samples for model training
1.6 Store training arrays and normalization parameters

## Part 2: Deep Learning Model: Training and Transfer
2.1 Define and train a U-Net-like convolutional neural network
2.2 Normalize input channels and scale target water depths
2.3 Apply the trained model to the first study area
2.4 Transfer the trained model to the second study area
2.5 Optionally fine-tune the model on additional target-area patches
2.6 Export spatially continuous prediction rasters

## Part 3: Calibration and Visualization
3.1 Align prediction and reference rasters on a common grid
3.2 Apply post-hoc calibration methods (e.g. Quantile Mapping, linear calibration)
3.3 Evaluate regression, classification, area and volume metrics
3.4 Compare raw and calibrated flood-depth predictions
3.5 Generate threshold-based performance tables and confusion maps
3.6 Export figures, GeoTIFFs and summary tables for presentation and reporting

Data preparation is listed in the PDF file: hyd_mod_workflow_lingglaham
Data evaluation, figures and Graphs are listed in the Folder structure and analysed in R (code attached)
