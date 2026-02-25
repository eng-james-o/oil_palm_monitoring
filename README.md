# Oil Palm Tree Detection and Counting

## Project Overview

This project aims to develop a machine learning model for detecting and counting oil palm trees in aerial or satellite imagery. The primary goal is to support agricultural monitoring and yield estimation by automating the identification of oil palm trees in large-scale geospatial data. By leveraging computer vision and geospatial analysis, the project seeks to provide accurate tree counts that can inform farming practices, resource allocation, and yield predictions.

The project utilizes high-resolution TIFF imagery and associated geospatial data (shapefiles) to train a Convolutional Neural Network (CNN) for binary classification of image patches containing oil palm trees versus non-trees.

## Goals

- **Agricultural Monitoring**: Enable real-time monitoring of oil palm plantations to track tree health, density, and distribution.
- **Yield Estimation**: Provide data-driven insights for estimating oil palm yields based on tree counts and spatial patterns.
- **Automation**: Reduce manual labor in tree counting by automating detection from imagery.
- **Scalability**: Develop a model that can be applied to large areas of land using satellite or drone imagery.

## Features

- Geospatial data processing using libraries like Rasterio and GeoPandas.
- Image patch extraction for positive (tree) and negative (non-tree) samples.
- CNN-based classification model built with TensorFlow/Keras.
- Visualization of detected trees on maps.
- Support for ROI (Region of Interest) cropping and boundary clipping.

## Requirements

- Python 3.8+
- Libraries: TensorFlow, Keras, Rasterio, GeoPandas, Shapely, NumPy, Pandas, Matplotlib, Scikit-learn
- Jupyter Notebook for running the development scripts

Install dependencies via pip:

```bash
pip install tensorflow rasterio geopandas shapely numpy pandas matplotlib scikit-learn
```

## Data

The project uses the following data sources located in the `training_data/` directory:

- **Imagery**: `image.tif` - High-resolution TIFF image of the oil palm plantation.
- **Trees Shapefile**: `trees/trees.shp` - Point data representing individual oil palm tree locations.
- **Boundary Shapefile**: `bounds/boundary.shp` - Polygon defining the plantation boundaries.
- **Annotations**: Text files with additional annotations (e.g., `annotations.txt`).

Data is processed to extract training patches:

- Positive samples: Patches centered on tree locations.
- Negative samples: Random patches without trees, ensuring no overlap with positive samples.

## Usage

1. **Data Preparation**:
   - Load and preprocess geospatial data.
   - Crop imagery to Region of Interest (ROI).
   - Extract positive and negative training patches.

2. **Model Training**:
   - Run the Jupyter notebook `experiments/Oil-palm-CV.ipynb` to train the CNN model.
   - The notebook includes steps for loading data, splitting into train/test sets, and training the model.

3. **Prediction**:
   - Use the trained model to predict on new imagery.
   - Visualize detected trees with bounding boxes.

Example command to run the notebook:

```bash
jupyter notebook experiments/Oil-palm-CV.ipynb
```

## Current State of the Work

The project is in the development phase with a functional prototype implemented in the Jupyter notebook `experiments/Oil-palm-CV.ipynb`. Key accomplishments include:

- **Data Loading and Preprocessing**: Successfully loads TIFF imagery, shapefiles, and processes geospatial transformations. Crops data to a defined ROI and clips to boundary polygons.
- **Patch Extraction**: Generates positive training samples from tree locations and negative samples from random non-overlapping areas. Uses IoU (Intersection over Union) to ensure no overlap between positive and negative patches.
- **Model Development**: A basic CNN model has been defined and trained for binary classification (tree vs. non-tree). The model uses Conv2D layers, MaxPooling, and Dense layers with dropout for regularization.
- **Evaluation**: Initial model training and evaluation are implemented, including accuracy metrics and visualization of training history.
- **Prediction and Visualization**: The model can predict on new image regions and overlay detected bounding boxes on the imagery.

The current implementation achieves basic functionality but has room for improvement in accuracy, speed, and robustness.

## Next Steps

To advance the project towards production-ready agricultural monitoring and yield estimation:

1. **Model Improvement**:
   - Experiment with pre-trained models (e.g., VGG16, ResNet) for better accuracy.
   - Implement data augmentation to increase training data diversity.
   - Fine-tune hyperparameters and add regularization techniques.

2. **Data Expansion**:
   - Collect more diverse imagery and annotations from different plantations.
   - Incorporate multi-temporal data for monitoring tree growth over time.
   - Add ground truth for yield data to correlate tree counts with actual yields.

3. **Advanced Features**:
   - Implement object detection (e.g., YOLO, Faster R-CNN) instead of patch-based classification for more precise localization.
   - Add tree health assessment using spectral indices or additional bands.
   - Integrate with GIS tools for full plantation management.

4. **Deployment and Integration**:
   - Develop a web-based interface or API for easy model deployment.
   - Integrate with cloud platforms (e.g., Google Earth Engine) for large-scale processing.
   - Automate the pipeline for real-time monitoring using drone or satellite data feeds.

5. **Validation and Testing**:
   - Conduct field validation to compare model predictions with manual counts.
   - Perform cross-validation and error analysis to identify model weaknesses.
   - Add unit tests and CI/CD pipelines for code reliability.

6. **Documentation and Collaboration**:
   - Expand this README with detailed API documentation.
   - Create tutorials and examples for users.
   - Open-source the project and encourage community contributions.

## Contributing

Contributions are welcome! Please fork the repository and submit pull requests. For major changes, open an issue first to discuss proposed modifications.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Contact

For questions or collaborations, please reach out to [Your Name/Email].
