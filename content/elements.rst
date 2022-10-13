.. _elements:

.. important:: In 2022-10, a more exact definition of the regularization was implemented in **gginv3d.exe** for sparse-norm inversion. The package containing the improved executable was released as **GG3D v6.0.1**. Be aware that GG3D v6.0 and v6.0.1 have all the same features and use the same executable names. Differences in the recovered model using each package were found to be insignificant.

Elements of the GG3D v6.0/v6.0.1 Package
========================================

This section provides a brief description of each program in the GG3D v6.0/v6.0.1 library. In addition, we describe the file formats for all input and supporting files used by the coding library.

Introduction
------------

The program library consists of the programs:

    - **ggfor3d.exe**: A code for forward modeling gravity gradiometry data from a density contrast model model.

    - **ggsen3d.exe**: calculates the sensitivity matrix for the inversion and outputs sensitivity weights.

    - **gginv3d.exe**: performs 3D inversion of gravity gradiometry data to recover a density contrast model.

    - **ggpre3d.exe**: multiplies the sensitivity file by the model to get the predicted data. This rarely used utility multiplies a model by the sensitivity matrix in to produce the predicted data. This program is included so that users who are not familiar with the wavelet transform and the structure of can utilize the available sensitivity matrix to carry out model studies.

Utility codes relevant to this package include:

   - **blk3cell.exe:** A utility for generating block models on tensor meshes

   - **pfweight_60.exe:** A utility for computing depth or distance weighting for potential field inversion


Main Input Files
----------------

Here, we describe the main input files for executables contained with the GG3D v6.0/v6.0.1 coding package.

.. toctree::
    :maxdepth: 1

    Create Model <inputfiles/createModel>
    Forward Modeling <inputfiles/forward>
    Depth/Distance Weighting <inputfiles/pfweights>
    Sensitivity Matrix <inputfiles/sensitivity>
    Inversion <inputfiles/inversion>


General files for GG3D programs
---------------------------------

Here, we describe the formats of supplementary files used to run GG3D v6.0/v6.0.1.

.. toctree::
    :maxdepth: 1

    Mesh <files/meshfile>
    Model <files/model>
    Topography <files/topo>
    Observation/Location <files/obs>
    Weighting <files/weight>

