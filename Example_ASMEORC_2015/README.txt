"""
ASME ORC 2015
3rd International Seminar on ORC Systems
12-14 October 2015, Brussels, Belgium

Example of detailed ORC with regenerator  model with subcooling and charge 
based solvers. The linesets are included for the charge estimation, but not 
to evaluate pressure drops between main cycle components. 
Minor adjustments can be done inside Cycle.py to account for lineset pressure drops

Reference Paper:
D. Ziviani et al. "ORCSIM: a generalized organic Rankine Cycle Simulation Tool". Paper#30
  
"""

To run the simulation code:

Preliminary: install conda (http://conda.pydata.org/docs/) or equivalent Python 

1) Git pull the "ORC--Example" folder from https://github.com/TSTK
1) install CoolProp for Python: http://coolprop.sourceforge.net/coolprop/wrappers/Python/index.html#python
2) Run the file Cycle_solve.py



Description of the files included:

PHEX_ASME2015 ::: contains a generalized moving-boundary algorithm applied to a plate heat exchanger. The code has been modified from the one available within ACHP (https://github.com/TSTK/ACHP) to include incompressible fluids of CoolProp. A condenser and an evaporator examples are provided at the end of the file ready to run.
Expander.py ::: contains a positive displacement expander model based on Pacejka equation for isentropic efficiency and log-type of correlation for the filling factor. More information about the mathematical modeling can be found in Declaye et al. "Experimental study on an open-drive scroll expander integrated into an ORC (Organic Rankine Cycle) system with R245fa as working fluid". An example of single-screw expander is provided.  
Pump_Centrifugal_Kortrijk.py ::: a centrifugal pump model is implemented based on two correlations for mass flow rate and isentropic efficiency.
Pump.py ::: additional pump model developed for volumetric pumps
LineSet.py ::: model of lineset with pressure drops calculations
LiquidReceiver.py ::: simplified model of a liquid receiver to estimate static pressure drop and the volume (charge as consequence) of the receiver.
first_guess_cycle.py ::: a preconditioner is implemented to obtain reasonable values for condensing and evaporating temperatures (eventually pressures) and the inlet state of the regenerator.
Cycle.py ::: the individual components are connected together. 
Cycle_solve.py ::: Running example of an ORC model based on ORC test set up located at Ghent University Campus Kortrijk (Belgium).
		   More information: Gusev et al. "EXPERIMENTAL COMPARISON OF A SINGLE SCREW EXPANDER UNDER DIFFERENT OPERATING CONDITIONS AND WORKING FLUIDS". ASME ORC 2015 #163

Additional files:
ACHPTool.py ::: data management and data saving routines (e.g. Write2CSV). Modified from original ACHPTool.
Correlations.py ::: heat transfer and pressure drops correlations
counter.py ::: an iteration counter
Solver.py ::: Multi-dimensional Newton-Raphson solver


Development:
the code is written by taking advantage of the object oriented capabilities of Python. More components can be easily added by modifying the existing library. The solution schemes for ORC w/ and w/out regenerator are general and the convergence criteria can be modified.


