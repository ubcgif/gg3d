.. _gg3d_inv:

.. important:: In 2022-10, a more exact definition of the regularization was implemented in **gginv3d.exe** for sparse-norm inversion. The package containing the improved executable was released as **GG3D v6.0.1**. Be aware that GG3D v6.0 and v6.0.1 have all the same features and use the same executable names. Differences in the recovered model using each package were found to be insignificant.

Inversion Program
=================

Running the Program
^^^^^^^^^^^^^^^^^^^

The inversion is run by opening a command line window and typing the path to the code **gginv3d.exe**, followed by a space, followed by the path to the :ref:`input file <gg3d_inv_input>` (denoted here as **inv.inp**). Optionally, the use made also include the number of threads. The syntax is as follows.

.. figure:: images/run_inv.PNG
    :align: center
    :width: 600

The argument specifying the number of CPU threads used in the OpenMP format is optional. If this argument is not given to the program, chooses to use all of the CPU threads on the machine. This argument allows the user to specify half, for example, of the threads so that the program does not take all available RAM. Note that this option is not available in the MPI-based code used for clusters.


Units:
------

**Input and outputs:**

    - **Data:** gravity gradiometry data in Eotvos
    - **Model:** density contrast model in g/cc

Output Files
------------

The program **gginv3d.exe** creates the following output files:

    - **gginv3d.log**: The log file containing the minimum information for each iteration and summary of the inversion.

    - **gginv3d.out**: The "developers" log file containing the details of each iteration including the model objective function values for each component, number of conjugate gradient iterations, etc.

    - **gginv3d_xxx.den**: Density constrast :ref:`model files <modelFile>` output after each "xxx" iteration (i.e., **gzinv3d_012.den**)

    - **gginv3d_xxx.pre**: :ref:`Predicted data files <ggfile>` (without uncertainties) output after each "xxx" iteration.






