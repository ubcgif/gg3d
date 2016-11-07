.. _ggpre3d:

GGPRE3D
=======

This utility multiplies a model by the stored sensitivity matrix (all components) to produce predicted data. This program is included so that users who are not familiar with the wavelet transform and the structure of could utilize the available sensitivity matrix to carry out modelling exercises. The command line usage is:

``ggpre3d gginv3d.mtx obs.loc model.den``

Input files
-----------

#. ``gginv3d.mtx``: The sensitivity matrix file create from :ref:`ggsen3d`.

#. ``obs.loc``: The gradiometry :ref:`location file <ggLocFile>`.

#. ``model.den``: The density contrast :ref:`model file <modelFile>`.


Output file
-----------

The output file is a :ref:`predicted data file <ggPreFile>` (omitting uncertainty column) and is named ``ggpre3d.gg``. This program can be used to reproduce output predicted files from :ref:`gginv3d`.


