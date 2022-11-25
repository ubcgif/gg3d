.. important:: The features and executable names within the GG3D the v6.0, v6.0.1 and v6.0.2 packages remain the same. Differences in version number correspond to improvements in performance and computational efficiency.


GG3D v6 Package
===============

GG3D v6 is a program library for carrying out forward modelling and inversion of surface, borehole, and airborne gravity gradiometry data in 3D.


Highlights
^^^^^^^^^^

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


