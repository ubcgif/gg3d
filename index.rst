.. GG3D documentation master file

GG3D v6.0 Package
=================

GG3D v6.0 is a program library for carrying out forward modelling and inversion of surface, borehole, and airborne gravity gradiometry data in 3D.


Highlights of GG3D v6.0
^^^^^^^^^^^^^^^^^^^^^^^^^

Many advancements have been made since the previous version of this coding package. Highlights of GG3D v6.0 include:


    - the ability to forward model and invert surface, borehole, and airborne gravity gradiometry data in 3D
    - the data can be full-tensor gradiometer (FTG) or the raw components of the Falcon or VK1 systems. 
    - sensitivity weighting so that targets recovered through inversion are placed at the correct depth
    - the ability to recover compact and/or blocky models using sparse norms, in additional to smooth models using a standard least-squares approach
    - implementing wavelet compression to reduce the storage cost of the sensitivity matrix and allow the user to solve larger problems


Sponsorship
^^^^^^^^^^^

The current improvements have been funded by the GIFtools Consortium which included “Potential fields and software for advanced inversion” (2012-2020) sponsored by Teck, Glencore, BHP Billiton, Vale, Cameco, Barrick, Rio Tinto, and Anglo American.

Contents
^^^^^^^^

.. toctree::
    :numbered:
    :maxdepth: 2

    Package overview <content/overview>
    Background theory <content/theory>
    Elements <content/elements>    
    Running the programs <content/runPrograms>
    Example <content/examples>
    References <references>


