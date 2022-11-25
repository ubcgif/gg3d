.. _overview:

.. important:: The features and executable names within the GG3D the v6.0, v6.0.1 and v6.0.2 packages remain the same. Differences in version number correspond to improvements in performance and computational efficiency.

GG3D v6 Package Overview
========================

Highlights
----------

**General GG3D Package Highlights:**

    - the ability to forward model and invert surface, borehole, and airborne gravity gradiometry data in 3D
    - the data can be full-tensor gradiometer (FTG) or the raw components of the Falcon or VK1 systems
    - distance weighting so that targets recovered through inversion are placed at the correct depth
    - implementing wavelet compression to reduce the storage cost of the sensitivity matrix and allow the user to solve larger problems


**v6.0 Highlights:**

    - the ability to forward model and invert both total magnetic intensity and amplitude data
    - the ability to recover compact and/or blocky models using sparse norms, in additional to smooth models using a standard least-squares approach


**v6.0.1 Highlights:**

    - implementation of a more exact definition for the regularization


**v6.0.2 Highlights:**

    - general sensitivities that can be used for least-squares or sparse-norm inversion
    - improved wavelet compression which acts on weighted sensitivities
    - update preconditionner during IRLS iterations to reduce number of conjugate gradient solves


Description
-----------

GG3D is a program library for carrying out forward modelling and inversion of surface and airborne gravity gradiometry data over 3D structures. The program library carries out the following functions:

#. Forward modelling of the gravity gradiometry tensor response to a 3D volume of density contrast.

#. The model is specified in the mesh of rectangular cells, each with a constant value of density contrast. Topography is included in the mesh. The vertical gravity response can be calculated anywhere within the model volume, including above the topography to simulate ground or airborne surveys. There is also a capability to simulate and invert data collected beneath the surface (e.g. borehole surveys) and combinations of ground and borehole surveys.

   -  The inversion is solved as an optimization problem with the simultaneous goals of (i) minimizing a model objective function and (ii) generating synthetic data that match observations to within a degree of misfit consistent with the statistics of those data.

   -  To counteract the inherent lack of information about the distance between source and measurement, the formulation incorporates depth or distance weighting.

   -  By minimizing the model objective function, distributions of subsurface susceptibility contrast are found that are both close to a reference model and smooth in three dimensions. The degree to which either of these two goals dominates is controlled by the user by incorporating a priori geophysical or geological information into the inversion. Explicit prior information may also take the form of upper and lower bounds on the susceptibility contrast in any cell.

   -  The regularization parameter (controlling relative importance of
      objective function and misfit terms) is determined in either of
      three ways, depending upon how much is known about errors in the
      measured data.

   -  Implementation of parallel computing architecture (OpenMP) allows
      the user to take full advantage of multi-core processors on a CPU.
      A cluster-based code using Message Passing Interface (MPI) is also
      available. Notes on computation speed are found at the end of this
      section.

#. The large size of 3D inversion problems is mitigated by the use of
   wavelet compression. Parameters controlling the implementation of
   this compression are available for advanced users.

The initial research underlying this program library was funded principally by the mineral industry consortium "Potential Fields and Software for Advanced Inversion" (2012 - 2016) which was sponsored the following companies: Anglo American, Barrick, BHP Billiton, Cameco, Computational Geosciences Inc., Glencore, Newmont, Rio Tinto, and Vale.


Program library content
-----------------------

Executable programs
^^^^^^^^^^^^^^^^^^^

The program library consists of the programs:

    - **ggfor3d.exe**: A code for forward modeling gravity gradiometry data from a density contrast model model.

    - **ggsen3d.exe**: calculates the sensitivity matrix for the inversion and outputs sensitivity weights.

    - **gginv3d.exe**: performs 3D inversion of gravity gradiometry data to recover a density contrast model.

    - **ggpre3d.exe**: multiplies the sensitivity file by the model to get the predicted data. This rarely used utility multiplies a model by the sensitivity matrix in to produce the predicted data. This program is included so that users who are not familiar with the wavelet transform and the structure of can utilize the available sensitivity matrix to carry out model studies.

Utility codes relevant to this package include:

   - **blk3cell.exe:** A utility for generating block models on tensor meshes

   - **pfweight_60.exe:** A utility for computing depth or distance weighting for potential field inversion


Graphical user interfaces
^^^^^^^^^^^^^^^^^^^^^^^^^
GUI-based utilities for these codes only include model viewing. It is only available on Windows platforms and can be freely downloaded through the UBC-GIF website:

   - `MeshTools3D <http://www.eos.ubc.ca/~rshekhtm/utilities/MeshTools3d.zip>`__: a utility for displaying resulting 3D models as volume renderings. Density contrast volumes can be sliced in any direction, or isosurface renderings can be generated.

Licensing
---------

The code is currently only available to members of the "Potential Fields and Software for Advanced Inversion" consortium.

.. A **constrained educational version** of the program is available with the `IAG <http://www.flintbox.com/public/project/1605/>`__ package (please visit `UBC-GIF website <http://gif.eos.ubc.ca>`__ for details). The educational version is fully functional so that users can learn how to carry out effective and efficient 3D inversions of magnetic data. **However, RESEARCH OR COMMERCIAL USE IS NOT POSSIBLE because the educational version only allows a limited number of data and model cells**.

.. Licensing for an unconstrained academic version is available - see the `Licensing policy document <http://gif.eos.ubc.ca/software/licenses>`__.

.. **NOTE:** All academic licenses will be **time-limited to one year**. You can re-apply after that time. This ensures that everyone is using the most recent versions of codes.

.. Licensing for commercial use is managed by third party distributors. Details are in the `Licensing policy document <http://gif.eos.ubc.ca/software/licenses>`__.

Installing
----------

There is no automatic installer currently available for GG3D. Please follow the following steps in order to use the software:

#. Extract all files provided from the given zip-based archive and place them all together in a new folder such as ``C:\gg3d``

#. Add this directory as new path to your environment variables.

**NOTE**: Do not store anything in the "bin" directory other than executable applications and Graphical User Interface applications (GUIs).


Notes on computation speed
^^^^^^^^^^^^^^^^^^^^^^^^^^

-  For large problems, GZSEN3D is significantly faster than the previous single processor inversion because of the parallelization for computing the sensitivity matrix computation and inversion calculations. Using multiple threads for running the parallelized version resulted in sensitivity matrix calculation speedup proportional to the number of threads. The increase in speed for the inversion was less pronounced, but still substantial.

-  It is strongly recommended to use multi-core processors for running the sensitivity calculation and inversion. The calculation of the sensitivity matrix (:math:`\mathbf{G}`) is directly proportional to the number of data (thus two components is twice the number of locations). The parallelized calculation of the :math:`n` rows of :math:`\mathbf{G}` is split between :math:`p` processors. By default, all available processors are used. There is a feature to limit :math:`p` to a user-defined number of processors.

-  In the parallelized inversion calculation, :math:`\mathbf{G}^T \mathbf{G}` is multiplied by a vector, therefore each parallel process uses only a sub-matrix of :math:`\mathbf{G}` and then the calculations are summed. Since there is significant communication between the CPUs, the speedup is less than a direct proportionality to the number of processors. 

-  For incorporating bound information, the implementation of the projected gradient algorithm in version 6.0 is primarily that the projected gradient results in a significantly faster solution than the logarithmic barrier technique used in earlier versions of the potentia;-field inversion codes.


