# simD2D
OMNeT++ project to use simulte.

Requirements:

OMNeT++ simulator (4.3 and above), inet framework (3.4)

This project contains a simple D2D network for the simuLTE framework. The configurations files provide multiple configurations to test the effect of varying parameters on the network.

Steps: 

1. Create a new OMNeT++ project. (empty project with no src, simulation folders) (OR) Use OMNeT++ GUI to add this project using git and select OMNeT++ project when prompted.

2. In project properties, make sure to add the 'inet'project and the 'simulte projedct as references.

3. Build project

4. Start simulation using either of the provided INI files (basicD2D.ini or multiD2D.ini)

P.S: If you want to run parallel simulations (using opp_runall), make sure to add the simulte/src directory in the list of sources while executing the command.

For e.g.: 
Assuming all 3 projects (simD2D, simulte and inet) are present in the same directory. And the simD2D directory is the current directory,
To simulate the config: 'TestDistanceStored' (it has 260 simulation runs) from basicD2D.ini, the command would be:

opp_runall -j${nproc} ./simD2D -u Cmdenv -c TestDistanceStored -r 0..259 -n .:../inet/src/:../simulte/src/ basicD2D.ini

(the command 'nproc' is available natively in linux and in Windows via the minGW environment - It returns the number of logical cores provided by the CPU)

