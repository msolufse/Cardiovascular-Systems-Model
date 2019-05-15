# Cardiovascular-Systems-Model

Matlab Files

Running the model
DriverBasic.m		Solves the odes with either nominal or optimized parameter values

Uses:
Patient233.m		Reads in all the data for patient 233
load_global.m		Calculates all nominal parameter values given the data
dXdT_Smith.m		Right hand side of the ODEs


Sensitivity analysis
DriverBasic_sens.m	Computes sensitivity equations. Saves the sensitivity matrix.

Uses:
load_global.m		Calculates all nominal parameter values given the data.
senseq.m		Calculates the Jacobian numerically
model_sol.m	Called by senseq.m evaluates the model and solves the ode’s. Returns the quantity that you want to find the sensitivity wrt. Currently it returns the model residual (line 128)
dXdT_Smith.m		Right side of the ODEs


Correlations
Covariances.m		Reads the sensitivity matrix and checks parameter correlations


Optimization
DriverBasic_optimization.m	Estimates parameters in the subset identified by covariances

Uses:
Cvmodel_wrap.m	Wrapper concatenates optimized parameters with all parameters
model_sol.m	Called by fmincon.m evaluates the model and solves the ode’s. Returns the least squares error
dXdT_Smith.m		Right side of the ODEs

After optimization is completed you run DriverBasic.m loading the optimized parameters and then you can plot results with plotres.m
