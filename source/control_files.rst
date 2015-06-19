#########################
Control files description
#########################

**********************
JGenerilo control file
**********************

The JGenerilo tool generate the emulated system topology on FPGA device based
on the control xml file. This file contains also placement of the thermometers
on the board. Below is presented an example of control file which has to be
added as first argument of the JGenerilo program. This file is also generated
by **FloorplanMaker**.

Example of correct control file
===============================

.. literalinclude:: _static/code_examples/generilo.xml
   :language: xml
   :name: control_generilo.xml

Correct file has to contain following tags:
 
* **board** - this tag contains information about the destination *device* (in
  current version user can use only virtex5 architecture), here user has also
  to choose applicable mode for generating floorplan (for now only *emulation*).

* **input** - information about source *.ncd* file (relative to location of XML
  file) to which we add heaters floorplan and thermometers.  

* **output** - destination file of created emulation system.  
  
* **heater** - description of ring oscilators grouped as one heater instance -
  this block correspond one block in HotSpot *.flp* file (HotSpot_: *.flp* file
  is file describing the floorplan of simulated device in HotSpot) or one
  functional block of real processor. 

.. _HotSpot: http://lava.cs.virginia.edu/HotSpot/ 
  
* **clb** - in heater's children tags user has to define which clbs are part of
  the heater (define the location of heater clb) and indicate the type of ring
  oscillator (In current version user can indicate only RO1 as a heater). 
  
* **thermometer** - description of one thermometer which is not a part of heater.
  User has to define the thermometer location and its type (In current version
  only available thermometer type is RO7)

*******************************
Simulio simulation control file
*******************************

User define the emulation program in a *.xml* file, below we present an
example of correct control file:

Example of correct control program file
=======================================

.. literalinclude:: _static/code_examples/simulio.xml
   :language: xml
   :name: control_simulio.xml

Correct file has to contain following tags:

* **program** - parent tag for all action tags in simulation program.

* **output** - this tag defines the destination file of thermometers
  measurements. 
  
* **settings** - in this tag in attribute ``duration`` user defines duration of
  experiment (available formats:s,min,h) 
  
* **heater** - this tag defines program for choosen heater instance defined
  before in Generilo control file. The correct order of heaters is required. 
  
* **conf** - contains information about heater power and the time point in
  which this power should by set up (the conf ``<conf power="70%"
  time="210min"/>`` means that we want setup ``70%`` power after ``210``
  minutes after emulation starts).  The minimal time pattern is second "s", the
  maximum pattern is hour ``h``.

***************************
FPGA build description file
***************************

FPGA build description file defines which blocks in the FPGA device are not
available (in general obstacles are blocks which user cannot use since they are
IO, DCM, BRAM, MUL and so on. Units are blocks occupied by logic connected with
SimulationCore logic or Microblaze). This file tells user which blocks are
available and can by used in heat floorplaning process. It is also used by
FloorplanMaker tool.

Example of correct FPGA description file
========================================

.. literalinclude:: _static/code_examples/floorplan.xml
   :language: xml
   :name: control_floorplan.xml

Correct file has to contain following tags:

* **size** - Size of FPGA (expressed in the number of function blocks)
  
* **clbsize** - size of cell logic block (CLB) ( in meters )
    
* **obstacle** - obstacles are blocks which user cannot use since they are IO,
  DCM, BRAM, MUL and so on beacuse they are structural blocks of FPGA device.

* **unit** - blocks occupied by emulation logic or for example Microblaze.
