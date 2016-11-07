.. _ggfor3d:

GGFOR3D
=======

This program performs forward modelling. Command line usage:

``ggfor3d mesh.msh obs.loc model.den [topo.dat]``

and will create the forward modelled data file ``ggfor3d.gg``. 

**NOTE**: The program will ignore values less than -90 g/cc in the model file. Therefore, files with values of -100 (the flag for above topography) from the inversion code will not contribute to the forward modelling.

Input files
-----------

All files are in ASCII text format - they can be read with any text editor. Input files can have any name the user specifies. Details for the format of each file can be found in Section [Elements]. The files associated with are:

- ``mesh.msh``: The 3D :ref:`mesh <meshfile>`.

- ``obs.loc``: The observation :ref:`locations <ggfile>`.

- ``model.den``: The density contrast :ref:`model <modelfile>` in g/cc.

- ``topo.dat``: Surface :ref:`topography <topofile>` (optional). If omitted, the surface will be treated as being flat and the top of the 3D mesh.

Output file
-----------

The created file is ``ggfor3d.gg``. The file format is that of the :ref:`data file <ggfile>` without the associated standard deviations. The forward modelled data are in **Eotvos**.

