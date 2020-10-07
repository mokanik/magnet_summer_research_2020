# magnet_summer_research_2020
Simulation files and preliminary report of remote summer internship with Dr Anson Cheung. 

Description of files/folders:

- folder: mathematica_notebooks - all Wolfram Mathematica (WM) files, contains "finite_thin(ish)_tube_off/on-axis.nb" - equivalents of Python notebooks tube_off/on-axis.ipynb, no Mathematica file treats the rotating magnet case (so far...)

- tube_nonparallel_magnet_leapfrog/RK4 - two shots at simulating rotating ("nonparallel") magnet using two different algorhitms, RK4 file is the "flagship" of this research, but is not yet verified / working properly

- tube_offaxis.ipynb - non-rotating, but free to move in xz plane

- tube_onaxis.ipynb - non-rotating, moving only along z-axis at x = y = 0, no automatic system for storing simulation arrays into files as in offaxis and nonparallel

folders with simulation data:
data from tube_offaxis and nonparallel... are automatically written into folders like e.g. 1_N200_iter2000_t2_x0 , where some chosen physical and simulation parameters appear in the name, to easily identify it and distinguish it from others in a series (e.g. x(0) may vary and give rise to names such as ...x0 for x(0) = 0 and ...x4 for x(0) = 4, etc.), files of  form 1_qty_N200_iter2000_t2_x0 , where qty is a physical quantity (an array from simulation) that is stored in that file - it can be J (current), x, z, vx, vz... . Length of all these file-arrays is "max_iter" , a simulation setting which defines the total number of iterations in time. Each folder also contains one file of form 1_info_N200_iter2000_t2_x0, which has all the necessary properties of the simulation listed (not just those encoded in file name).

- folder: python_arrays_offaxis - results of simulations from file tube_offaxis.ipynb
etc....
