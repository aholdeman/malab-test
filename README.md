## Running MATLAB

MATLAB is a high-level language and interactive environment for numerical computation, visualization, and programming. Here is a demonstration of running MATLAB in batch mode.

1. Create a MATLAB script. This repository provides a simple script, <i>matlabtest.m</i>, which generates a matrix, randomly populates it, finds the inverse, and then computes the product of the two matrices.

2. Prepare the submission script, which is the script that is submitted to the Slurm scheduler as a job in order to run the MATLAB script. This repository provides the script <i>job.sh</i> as an example.

3. Submit the job using `sbatch job.sh` 

4. Examine the results
