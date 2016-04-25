# Tuna

Tuna is a 2.5D simulation of Alfven waves in the inner magnetosphere. It's written by Charles McEachern, based on work by Bob Lysak.

The code is thoroughly documented inline. More information can be found in published works, such as Lysak's 2013 paper in JGR or McEachern's 2016 dissertation. 

## `source.f90`

The code is written in Fortran. All modules are packed into a single file. 

## `driver.py`

The driver is a Python script which conducts one or more runs with Tuna, based on the input parameters at the top of the script. 

For each run, the driver creates a timestamped output directory. It then compiles the source code, copies over the necessary ionospheric profiles, and creates the input file `params.in`. If running on a local machine, the driver carries out the run and checks for a crash; if run on a supercomputer, it instead creates a PBS script and submits the run to the queue. 

Several parameters in `driver.py` are set up with the assumption that the user is `mceachern@eelpout.spa.umn.edu` or `mceache1@itasta.msi.umn.edu` -- these will need to be changed for the script to work for anyone else.

## `plotter.py`

The plotter is a Python script which creates visualizations from Tuna's output. It can handle lines, contours, color meshes, and bar plots. It's designed in particular to make it easy to put together a lattice of subplots. 

It's a bit kludgey right now. It's a work in progress. 

## `plotmod.py`

The plotting backend is all in the plot module. It's shared between Tuna and the RBSP repository, though the two versions have slightly diverged. The Charlesplotlib repo (under construction) is intended to be a consistent plotting library used by both. 


