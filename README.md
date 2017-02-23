# simD2D
<H1>OMNeT++ project to use simulte.</H1>

<H3>Requirements:</H3>

* OMNeT++ simulator (4.3 and above)
* inet framework (3.4)

This project contains a simple D2D network for the simuLTE framework. The configurations files provide multiple configurations to test the effect of varying parameters on the network.

<H3>Steps:</H3>

1. Create a new OMNeT++ project. (empty project with no src, simulation folders) (OR) Use OMNeT++ GUI to add this project using git and select OMNeT++ project when prompted.

2. Go to project properties, add the 'inet' project and the 'simulte' project as references.

3. Build the project.(uske make from command line or build the rpoject using the OMNeT++ GUI)

4. Start simulation using either of the provided INI files (basicD2D.ini or multiD2D.ini)

<H4>P.S: If you want to run parallel simulations (using opp_runall), make sure to add the 'simulte/src/' directory in the list of sources while executing the command.</H4>

For e.g.:  
Assuming all 3 projects (simD2D, simulte and inet) are present in the same directory. And the simD2D directory is the current directory,  
To simulate the config: _TestDistanceStored_ (it has 260 simulation runs) from __basicD2D.ini__, the command would be:

`opp_runall -j$(nproc) ./simD2D -u Cmdenv -c TestDistanceStored -r 0..259 -n .:../inet/src/:../simulte/src/ basicD2D.ini`

(the command _nproc_ is available natively in linux and in Windows via the bash shell found in developer mode for Windows 10 (or) via minGW/cygwin environment  - It returns the number of logical cores provided by the CPU.)  

You can replace _nproc_ by an integer value depicting the number of cores you would want to use for running the parallel simulations (please ensure that you have sufficient memory while running parallel simulations).

For eg., to use 4 cores for the parallel simulation, replace __-j$(nproc)__ by __-j4__

