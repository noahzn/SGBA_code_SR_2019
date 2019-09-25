# SGBA_code_SR_2019

This section presents all the repositories necessary for recreating the simulation and the real-world experiments. For the submission version, all the repositories can be found in the folder ‘git_repositories’ on surfdrive:
 https://surfdrive.surf.nl/files/index.php/s/KKJHTW3zTPIVj5N 
	 Password: kd*#JD18uo)!NF
 
	Simulation
This section shows the git-repositories for the simulation experiments. (for the initial submission, the urls to the github-repositories do not work as they are not public, see the URL given above). Please check Fig. S1 for a simple representation of the ROS nodes:
	ARGoS_bridge (ROS kinetic): https://github.com/tudelft/ARGoS_bridge (branch: gradient_bug_testing)
	The node to port ROS twist-commands to the foot-bot and returns the laser-range finder measurements.
	Indoor_environment_generator (ROS kinetic): https://github.com/tudelft/indoor_environment_generator (branch: master)
	The ROS package contains the procedural random indoor environment generator and provides the simulated RSSI measurements for the ARGoS’s foot-bot.
	ARGoS: https://github.com/tudelft/ARGoS3 (branch: ARGoS3_mod_tudelft)
	Contains the modified foot-bot model.
	Bug_Algorithms (ROS kinetic): https://github.com/tudelft/bug_algorithms (branch: master)
	Contains the finite state machine for the standard bug algorithms.
	Gradient_bug (ROS kinetic): https://github.com/tudelft/gradient_bug (branch: master)
	Contains the state machine for the swarm gradient bug algorithm.
How to use with ROS kinetic: 
	In a terminal, type “roslaunch bug_algorithms launch_bug_algorithm.launch”
	In another terminal, type “python multiple_environments_test.py” to supervise the tests.

	Real-World Testing
This section shows all the github-repositories necessary for the real-world experiments:
	Crazyflie_firmware: https://github.com/tudelft/crazyflie-firmware-private  (branch: systemtest_gradientbug)
	This repository contains all the necessary changes to the Crazyflie firmware in order to make the SGBA work onboard
	Crazyflie2-nrf-firmware: https://github.com/tudelft/crazyflie2-nrf-firmware   (branch: systemtest_gradientbug)
	This repository contains the firmware of the NRF51 chip on the Crazyflie 2.0, in order to enable inter-drone communication.

How to start up the experiment:
	Give the Crazyflie a unique ID: E7E7E701, E7E7E702, etc.
	First flash the NRF and STM chips of all the Crazyflie with the following bashscript: ‘gradient_bug/bashscripts/flash_all_crazyflies.sh’
	Start the real-world testing with the following bashscript: ‘gradient_bug/bashscripts/start_swarm_exploration_experiment.sh’
	If something goes wrong, close the last bashscript and run ‘land_all.sh’
