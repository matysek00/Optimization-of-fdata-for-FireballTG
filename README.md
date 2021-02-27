# Optimization-of-fdata-for-FireballTG
The optimization and simple creation of fdata for FireballTG (https://nanosurf.fzu.cz/wiki/doku.php?id=fireball). 

## Libraries and other Instalations
Fireball
* https://github.com/fireball-QMD/progs

Cuby
* https://github.com/berquist/cuby
* To compare the results from Fireball to selected benchmarks. 
* Not necessery if the code is used only to create Fdata but not to optimize them. 

Python 3.6.9 Libraries
* numpy
* scipy

## Instalation 
 ...
 
## Usage 
Always make sure that there is a file where all atoms and their paramaeters are defined (see atoms.in) before running. When runnig CreateFdata.py it is enough to define only mark and name of each atom, if the remainnig paramaters are defined from the terminal, when calling the script. You can also overwrite the parameter value when calling the function. When running OprimizeFdata.py all parameters must be defined in the input file for each used atom. 
### Create Fdata
When only creating fdata with given paramaters
<pre>
CreateFdata.py [-h] [-i INFILE] [-o OUTFILE] [-x XC] [-n NCPUS]
                AtomChoice [AtomChoice ...]

Finds the best parameters for fdata

positional arguments:
  AtomChoice            atoms to be used in the Fdata if any parameters are
                        different than in input file use 'H --par1 x1 --par5
                        x5 etc.'

optional arguments:
  -h, --help            show this help message and exit
  -i INFILE, --infile INFILE
                        input file with descriptions all of atoms
  -o OUTFILE, --outfile OUTFILE
                        where to write the output
  -x XC, --xc XC        The correlation fuctional if not chosen used as
                        defined in infile
  -n NCPUS, --ncpus NCPUS
                        number of CPUs, default is 1
</pre>
If only 1 CPU was used the fdata will then apear in create/coutput. If more CPUs were used the fdata will then apear in create_mpi/coutput.

### Optimize Fdata
To find paramaters with witch the fireball calculations best fit to given benchmarks. 
First edit the test/input.yaml file to chose what system should cuby compare fireball to. Next run the OptimizeFdata.py
<pre>
CreateFdata.py [-h] [-i INFILE] [-o OUTFILE] [-x XC] [-n NCPUS]
                AtomChoice [AtomChoice ...]

Finds the best parameters for fdata

positional arguments:
  AtomChoice            atoms to be used in the Fdata if any parameters are
                        different than in input file use 'H --par1 x1 --par5
                        x5 etc.'

optional arguments:
  -h, --help            show this help message and exit
  -i INFILE, --infile INFILE
                        input file with descriptions all of atoms
  -o OUTFILE, --outfile OUTFILE
                        where to write the output
  -x XC, --xc XC        The correlation fuctional if not chosen used as
                        defined in infile
  -n NCPUS, --ncpus NCPUS
                        number of CPUs, default is 1
</pre> 
The result and progess will be written into the outfile. 
