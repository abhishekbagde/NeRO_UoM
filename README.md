# NeRO_UoM: Neural Reflectance Optimization for Cultural Heritage Digitization

This repository hosts the enhanced NeRO (Neural Reflectance Optimization) pipeline, developed and tailored for cultural heritage digitization, specifically for the [John Rylands Library](https://www.library.manchester.ac.uk/rylands/) at the [University of Manchester](https://www.manchester.ac.uk/). The pipeline incorporates Structure-from-Motion (SfM) techniques, high-performance computing integration, and neural rendering to produce high-fidelity 3D models of artifacts.

## New Features

- **Parallelization and GPU Acceleration**: Optimized for batch processing in HPC environments using GPU acceleration.
- **End-to-End Pipeline**: The workflow is streamlined for multi-stage processing (feature extraction, reconstruction, BRDF estimation).
- **Enhanced Scalability**: Capable of handling large-scale datasets efficiently with [Computational Shared Facility (CSF)](https://www.itservices.manchester.ac.uk/research/csf/) integration.
- **Automated Metadata Generation**: Uses machine learning for generating metadata to facilitate cataloging.
- **User Interface Enhancements**: Simplified CLI with detailed logging for resource usage and debugging.

## Setup

1. **Clone this repository**:
   ```
   git clone https://github.com/abhishekbagde/NeRO_UoM.git
   cd NeRO_UoM
   ```

2. **Install Anaconda or Miniconda** on your system if not already installed.

3. **Dataset Preparation**: Ensure images follow the directory structure:
   ```
   NeRO/data/custom/object_name/images/
   ```

## Usage

To execute the full pipeline, run:

```
python nero_pipeline.py /path/to/image/folder /path/to/nero/directory
```

The pipeline consists of the following stages:
- **Feature Detection & Matching**: Initiates feature extraction with SIFT.
  ```
  nero_pipeline.py --dataset dataset_name --stage features
  ```
- **Sparse & Dense Reconstruction**: Generates a 3D point cloud and mesh.
  ```
  nero_pipeline.py --dataset dataset_name --stage reconstruction
  ```
- **BRDF Estimation**: Extracts material properties for realistic rendering.
  ```
  nero_pipeline.py --dataset dataset_name --stage nerf --brdf
  ```
- **Exporting the Model**: Exports the final model in OBJ/PLY format.
  ```
  nero_pipeline.py --dataset dataset_name --export-format obj ply
  ```

## Requirements

- Python 3.10+
- CUDA 11.7
- [COLMAP](https://colmap.github.io/)
- NeRO dependencies (specified in `requirements.txt`)
- University of Manchester’s [Computational Shared Facility (CSF)](https://www.itservices.manchester.ac.uk/research/csf/) for large-scale digitization

## Key Enhancements

- **HPC Integration**: Full integration with [CSF](https://www.itservices.manchester.ac.uk/research/csf/) for large-scale parallel processing, reducing time and carbon emissions.
- **Improved Reconstruction Quality**: Integrates NeRF models for challenging surfaces, enhancing detail and material properties.
- **Scalable Batch Processing**: Supports the digitization of multiple objects in parallel using the batch processing system.


## License

This project is licensed under the same terms as the original NeRO project. Refer to the `LICENSE` file for more information.

## Acknowledgments

- [NeRO development team](https://github.com/zju3dv/NeRO)
- [COLMAP](https://colmap.github.io/) and [VisualSFM](http://ccwu.me/vsfm/) developers
- [John Rylands Library Digitization Project](https://www.library.manchester.ac.uk/rylands/), [University of Manchester](https://www.manchester.ac.uk/)

For more information, refer to the detailed documentation in the thesis or the [original NeRO repository](https://github.com/zju3dv/NeRO).
