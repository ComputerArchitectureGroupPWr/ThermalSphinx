.. Thermal Project documentation master file, created by
   sphinx-quickstart on Mon Jun  8 08:48:20 2015.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to Thermal Project's documentation!
===========================================

The aim of the research project is to develop models and procedures for
simulation of thermal behavior of multi-core processors, using hardware
emulators. Existing simulators of thermal behavior (e.g. HotSpot) model heat
dissipation by solving the state equation and evaluating temperature and power
for individual blocks of the simulated processor. The state equation takes into
account all sources of heat, thermal resistances and thermal capacities, and is
solved iteratively during the simulation. The disadvantage of such approach is
high computational complexity, which increases the simulation time, and limits
the complexity of processor’s models that can be efficiently simulated. In the
proposed solution we plan to replace the thermal state equation with emulation
implemented in a real electronic system. Emulation involves heating elements
and temperature sensors placed in the reconfigurable system. Distribution, size
and parameters of the heating elements model structure of the emulated
processor with an accuracy of a single basic block (e.g. adder). Heating
elements be used to reflect the thermal activity of individual functional
blocks by changing the quantity of emitted heat. Heat dissipation and the
associated temperature changes are recorded by sensors and transmitted to the
computer simulator which models the entire operation of the simulated processor
architecture. The advantage of this approach is elimination of time consuming
calculations which are associated with solving the state equation. Calculations
are replaced with real physical phenomena occurring inside the reconfigurable
system, in real time. This allows to accelerate the thermal emulation
significantly by shortening the time of transient thermal simulation and,
consequently, allowing to explore the behavior of multi-core processors modeled
in more detail.

Funding: National Science Centre , proj. no.: 2011/03/B/ST6/00343

Primary investigator: Bartosz Wojciechowski, Contact person: Bartosz Wojciechowski

******************
 Table of content
******************

.. toctree::
   :maxdepth: 2

   intro
   toolset
   getting_started
   support
   related_projects

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

