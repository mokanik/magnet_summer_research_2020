README_python relevant for python jupyter notebooks.
Date last updated: 06/09/2020

I have re-written my older Mathematica simulations in Python. The reason is that Mathematica's "NDSolve" does not allow numerical evaluation of expressions containing variables sought-after. This greatly complicates the process and it has rendered the mathematical system opaque (and seemingly not working!)

Note: self-inductance of ring/tube is at present neglected in calculations (e.m.f. comes solely from cutting flux of falling magnetic dipole field)



File "ring.ipynb" contains code for calculations for magnet falling centrally through a single ring in x-y plane. Four methods of calculation are tryed:
1) "odeint" function of SciPy - similar to "NDSolve" in Mathematica
2) basic finite diference method "x[t+dt] = x[t] + dt * x'[t]"
3) improved finite difference method "x[t+dt] = x[t] + dt * x'[t+1/2*dt]"
4) finite difference method which does not invoke matrices A,V, but instead expresses time derivatives from Z
    -use two point operator for A=Z'':  (Z[i+1] - 2*Z[i] + Z[i-1]) / dt**2 = g - 1/M * magForce(Z[i],J[i])
    -use central difference for V=Z': (Z[i+1] - Z[i-1])  / (2*dt) == Z'
To my surprise, all three FDMs 2)-4) had similar accuracy, just the last one being slightly faster than 2) and 3).
Results were compared to Mathematica notebook "ring_and_finite_tube.nb" as reference, and results were in good agreement, considerable agreement was obtained for roughy similar execution time than Mathematica's "NDSolve".


File "tube_on_axis.ipynb" contains code for calculations for magnet falling centrally through a tube centered on z-axis. Again, multiple calculation methods were tried with similar results, broadly in agreement with "finite_thin(ish)_tube_onaxis.nb".


File "tube_off_axis.ipynb" contains code for calculations for magnet falling off-axis through a tube centered on z-axis. Results are roadly in agreement with "finite_thin(ish)_tube_onaxis.nb". (Not too surprisingly) good resolution in time is more crucial than good resolution in spatial partitioning of the tube into rings, in order to get the best result possible in reasonable time. Execution time roughly linear in both time and space. On-axis results from previous file are well reproduced.