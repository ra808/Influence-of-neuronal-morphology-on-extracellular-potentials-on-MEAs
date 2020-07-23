# Influence-of-neuronal-morphology-on-extracellular-potentials-on-MEAs
# Copyright (c) 2020 Robert Bestel/ Revathi Appali

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the 'Software'), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
 subject to the following conditions:

 The above copyright notice and this permission notice shall be included in all
 copies or substantial portions of the Software.

# THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
 
# Author: Robert Bestel

This file describes the COMSOL implementation of neuronal models on MEA with electrode coupling developed in paper:

     R. Bestel, U. van Rienen, C. Thielemann, and R. Appali, “Measuring Neuronal Signals with Microelectrode Arrays: A Finite Element Analysis,”
     bioRxiv, 2020, doi: 10.1101/2020.06.07.139014. 
     Subitted to IEEE TBME

This directory contains three threedimensional neuron models to simulate extracellular recording of electric neuronal signals. 
The models use Hodgkin-Huxley model descriptions for action potential generation and propagation. 
The distribution of electric potential in intra- and extracellular space is modeled using an electro-quasistatic approximation of Maxwell's equation. 
An planar extracellular microelectrode embedded in an insulating surface is described using an equivalent circuit connected to the threedimensional domain. 
circular grain embedded inside a square domain. 

The directory consists of the files
     README
     
     model I_template.mph
     model II_template.mph
     model III_template.mph
     
     geometry model I.stl
     geometry model II.stl
     geometry model III.stl
     
     Parameters_model I.m
     Parameters_model II.m
     Parameters_model III.m
     
     expressions_model I.m
     expressions_model II.m
     expressions_model III.m

Following are steps to be followed to run one of the model x.mph:

1) Open any of the 'model x.mph' COMSOL file. The .mph file, in its current form, has the 
   parameters, variables and pdes already inputted. Using the 'solve' command in the study tab of COMSOL.
   Geometry, physics expressions or parameters can be altered in the respective directories.

2) Instead, if you intend to make any changes to the model by altering the expressions.m file, then the new 
   parameters.txt, variables.txt and the pde.txt files are to be included as follows
   
   Run 'expressions.m', a matlab file used to generate the following 
   three .txt files: 1) parameters.txt, 2) variables.txt and 3) pde.txt. These
   files are used as input for material parameters, variable definitions and weak
   form pdes in COMSOL v5.x file 'model x.mph'. :

   The files parameters.txt and variables.txt are uploaded in 
   the tabs (of COMSOL v5.x)

       Global Definitions -> parameters,
       Component 1 -> Definition -> variables,

   respectively. The weak-form pdes in the file 'pde.txt' are pasted into the respective
   PHYSICS tabs.
      
3) Run 'pcp_circular.mph'
