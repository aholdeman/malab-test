## MATLAB Tutorial

MATLAB is a high-level language and interactive environment for numerical computation, visualization, and programming. Using MATLAB, you can analyze data, develop algorithms, and create models and applications. The program can be used with the GUI or in batch mode. 

[Documentation for MATLAB can be found on its official website.](https://www.mathworks.com/help/matlab/)

Currently, MATLAB version R2017b is available on the cluster.

To use MATLAB through the command line, first load the MATLAB module, then use a command similar to:

`matlab -r myscript.m`

where _myscript.m_ is the MATLAB script you wish to run. 

To run MATLAB interactively (using the GUI), you must first enable transparent forwarding when connecting to the server using the -X option to the ssh command. Once logged in, start the MATLAB GUI by simply typing matlab into the command line. 

Below, you will find an example of how to run MATLAB using a job script.

1. Create a MATLAB script. The linked repository provides a simple script, matlabtest.m, which generates a matrix, randomly populates it, finds the inverse, and then computes the product of the two matrices.

#### matlabtest.m
`
% sets the size of the matrix to 4 x 4
n = 4;
% randomly populates the matrix with values
A = rand(n);
% print the result
A
% takes the inverse of the matrix
V = inv(A);
% print the result
V

% multiply by the original matrix to get the identity matrix
I = V*A
`

2. Prepare the submission script, which is the script that is submitted to the Slurm scheduler as a job in order to run the MATLAB script. The linked repository provides the script _job.sh_ as an example.

#### job.sh
`
#!/bin/bash

#SBATCH --job-name=matlab_test
#SBATCH -o matlab_out%j.out
#SBATCH -e matlab_err%j.err
#SBATCH -N 1
#SBATCH --ntasks-per-node=1

echo -e '\n submitted Matlab job'
echo 'hostname'
hostname

#loads the matlab module
module load matlab

#runs the matlabtest.m file using matlab, forwards results to results.txt
matlab -r matlabtest > results.txt
`

3. Submit the job using
	`sbatch job.sh`
  
4. Examine the results
