# miro_behaviour_config
An wrapper based on ROS parameter for MIRO's demos

This repository contains a wrapper of the [https://consequential.bitbucket.io/Developer_Examples_Python_GUI_Client.html](MIRO: Python GUI Client) that maps each flags in the `core` tab of the Graphical User Interface to a `boolean` ROS.

# Installation & run
- clone this repository in your `catkin` workspace
- dowload the [http://labs.consequentialrobotics.com/miro-b/software/](Miro mdk) and unzip it into the folder `~/mdk`
- in all your terminals (or in the `~/.bashrc` file) set
	- `export MIRO_PATH_MDK=~/mdk`
	- `export ROS_PACKAGE_PATH=$MIRO_PATH_MDK/share:$ROS_PACKAGE_PATH`
	- `export PYTHONPATH=$MIRO_PATH_MDK/share:$PYTHONPATH`
	- eventually, setup your `ROS_IP` and `ROS_MASTER_URI`
- set up your [https://consequential.bitbucket.io/Developer_Preparation_Commission_MIRO.html](workstation) for Miro
- install the Miro [https://consequential.bitbucket.io/Demonstrator_Configuring_MIROapp.html](Android) and run the bridge
- run the behavior configuration GUI `roslaunch miro_behaviour_config miro_behaviour.launch`

# Usage
If the steps above are successful you will see an GUI for giving commands to Miro as distributed from **Consequential Robotics**.
In this repository the check-boxes of the `core` tab will be synchronized to related ROS parameters, which are boolean and listed below.
Now you can change behaviors of Miro from ROS node, services and launchers online!

For a simple test use
```rosparam set /rob01/behaviour/flagConfig/BODY_ENABLE true``` 
and check the `core` tab in the GUI.
You schould run thi command only after that the `update core tab connection to rosparam` happeared in the terminal.

# Launcher
The repository contains a launcher that runs the `miro_behaviour_controller` node with the `robot` name and `gui_template` file path arguments
```
cd ros_ws/src/miro_behaviour_config/script/
rosrun miro_behaviour_config miro_behaviour_controller.py robot:=rob01 gui_template:=miro_ros_client_gui.glade
```

The node creates and synchronizes flags (initialized to `false`) in the ROS parameter server with a root name specified in the launcher as `MIRO_PARAM_ROOT` (which by default is `/rob01/behaviour/flagConfig/`).
The parameters that are synchronized with the GUI are:
- BRANCH_ENABLE
- AFFECT_ENABLE
- AFFECT_ADJUST_RTC
- AFFECT_VALENCE_DYNAMICS
- AFFECT_AROUSAL_DYNAMICS
- AFFECT_ENABLE_SLEEP
- AFFECT_FROM_CLOCK
- AFFECT_FROM_WAKEFULNESS
- AFFECT_FROM_TOUCH
- AFFECT_FROM_LIGHT
- AFFECT_FROM_SOUND
- AFFECT_FROM_ACCEL
- AFFECT_FROM_SLEEP_BLOCKED
- AFFECT_RANDOMIZE_VALENCE
- AFFECT_FAST_SLEEP_DYNAMICS
- EXPRESS_ENABLE
- EXPRESS_THROUGH_LIGHT
- EXPRESS_THROUGH_TAIL
- EXPRESS_THROUGH_EYELIDS
- EXPRESS_THROUGH_EARS
- EXPRESS_THROUGH_VOCAL
- EXPRESS_THROUGH_BODY
- DEBUG_SONAR
- EXPRESS_NO_PIRATE_NOISES
- EXPRESS_DO_PIRATE_NOISES
- ACTION_ENABLE
- ACTION_DEBUG
- ACTION_FORCE_MULL
- ACTION_RANDOMIZE_ORIENT
- ACTION_DISABLE_HALT
- ACTION_MODULATE_BY_SONAR
- BODY_ENABLE
- BODY_RESET_KC_INTEGRATORS
- BODY_NO_PUSH
- BODY_NO_PUSH_MOTION
- BODY_NO_PUSH_TRANSLATION
- BODY_NO_PUSH_INTO_SONAR
- ENABLE_POS_CONTROL
- ENABLE_CLIFF_REFLEX
- SPATIAL_ENABLE
- SPATIAL_IGNORE_AUDIO
- SPATIAL_IGNORE_VIDEO
- SPATIAL_SEND_PRIORITY
- SPATIAL_SEND_OTHER
- SPATIAL_NO_REAFF_COMPROMISE
- SPATIAL_NO_SUPPRESS
- SPATIAL_SHOW_COMPROMISE
- SPATIAL_SHOW_TEST_PATTERN
- TEST_ALARM


# Contacts
Luca Buoncompagni, EMAROlab, DIBRIS, University of Genoa.   
luca.buoncompagni@edu.unige.it
