# miro_behaviour_config
An wrapper based on ROS parameter for MIRO's demos

This repository contains a wrapper of the [https://consequential.bitbucket.io/Developer_Examples_Python_GUI_Client.html](MIRO: Python GUI Client) that maps each flags in the `core` tab of the Graphical User Interface to a `boolean` ROS parameter.

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
- run the behavior configuration GUI ```roslaunch miro_behaviour_config miro_behaviour.launch```

# Usage
If the steps above are successful you will see a GUI as distributed from **Consequential Robotics**.
In this repository the check-boxes of the `core` tab will be synchronized to related ROS parameters, which are boolean and listed below.
Now you can change behaviors of Miro from ROS nodes, services, launchers and terminals online!

For a simple test use
```rosparam set /rob01/behaviour/flagConfig/BODY_ENABLE true``` 
and check the relative falg in `core` tab in the GUI.
You schould run this command only after that your teminal logs `update core tab connection to rosparam`.

# Launcher
The repository contains a launcher that runs the `miro_behaviour_controller` node, which as as arguments: the `robot` name and `gui_template` file path,
```
cd ros_ws/src/miro_behaviour_config/script/
rosrun miro_behaviour_config miro_behaviour_controller.py robot:=rob01 gui_template:=miro_ros_client_gui.glade
```

The node creates and synchronizes flags (initialized to `False`) in the **ROS parameter server** with a root name specified in the launcher as `MIRO_PARAM_ROOT` (which by default is `/rob01/behaviour/flagConfig/`).
The parameters that are synchronized with the GUI are:
- `MIRO_PARAM_ROOT + "BRANCH_ENABLE"`
- `MIRO_PARAM_ROOT + "AFFECT_ENABLE"`
- `MIRO_PARAM_ROOT + "AFFECT_ADJUST_RTC"`
- `MIRO_PARAM_ROOT + "AFFECT_VALENCE_DYNAMICS"`
- `MIRO_PARAM_ROOT + "AFFECT_AROUSAL_DYNAMICS"`
- `MIRO_PARAM_ROOT + "AFFECT_ENABLE_SLEEP"`
- `MIRO_PARAM_ROOT + "AFFECT_FROM_CLOCK"`
- `MIRO_PARAM_ROOT + "AFFECT_FROM_WAKEFULNESS"`
- `MIRO_PARAM_ROOT + "AFFECT_FROM_TOUCH"`
- `MIRO_PARAM_ROOT + "AFFECT_FROM_LIGHT"`
- `MIRO_PARAM_ROOT + "AFFECT_FROM_SOUND"`
- `MIRO_PARAM_ROOT + "AFFECT_FROM_ACCEL"`
- `MIRO_PARAM_ROOT + "AFFECT_FROM_SLEEP_BLOCKED"`
- `MIRO_PARAM_ROOT + "AFFECT_RANDOMIZE_VALENCE"`
- `MIRO_PARAM_ROOT + "AFFECT_FAST_SLEEP_DYNAMICS"`
- `MIRO_PARAM_ROOT + "EXPRESS_ENABLE"`
- `MIRO_PARAM_ROOT + "EXPRESS_THROUGH_LIGHT"`
- `MIRO_PARAM_ROOT + "EXPRESS_THROUGH_TAIL"`
- `MIRO_PARAM_ROOT + "EXPRESS_THROUGH_EYELIDS"`
- `MIRO_PARAM_ROOT + "EXPRESS_THROUGH_EARS"`
- `MIRO_PARAM_ROOT + "EXPRESS_THROUGH_VOCAL"`
- `MIRO_PARAM_ROOT + "EXPRESS_THROUGH_BODY"`
- `MIRO_PARAM_ROOT + "DEBUG_SONAR"`
- `MIRO_PARAM_ROOT + "EXPRESS_NO_PIRATE_NOISES"`
- `MIRO_PARAM_ROOT + "EXPRESS_DO_PIRATE_NOISES"`
- `MIRO_PARAM_ROOT + "ACTION_ENABLE"`
- `MIRO_PARAM_ROOT + "ACTION_DEBUG"`
- `MIRO_PARAM_ROOT + "ACTION_FORCE_MULL"`
- `MIRO_PARAM_ROOT + "ACTION_RANDOMIZE_ORIENT"`
- `MIRO_PARAM_ROOT + "ACTION_DISABLE_HALT"`
- `MIRO_PARAM_ROOT + "ACTION_MODULATE_BY_SONAR"`
- `MIRO_PARAM_ROOT + "BODY_ENABLE"`
- `MIRO_PARAM_ROOT + "BODY_RESET_KC_INTEGRATORS"`
- `MIRO_PARAM_ROOT + "BODY_NO_PUSH"`
- `MIRO_PARAM_ROOT + "BODY_NO_PUSH_MOTION"`
- `MIRO_PARAM_ROOT + "BODY_NO_PUSH_TRANSLATION"`
- `MIRO_PARAM_ROOT + "BODY_NO_PUSH_INTO_SONAR"`
- `MIRO_PARAM_ROOT + "ENABLE_POS_CONTROL"`
- `MIRO_PARAM_ROOT + "ENABLE_CLIFF_REFLEX"`
- `MIRO_PARAM_ROOT + "SPATIAL_ENABLE"`
- `MIRO_PARAM_ROOT + "SPATIAL_IGNORE_AUDIO"`
- `MIRO_PARAM_ROOT + "SPATIAL_IGNORE_VIDEO"`
- `MIRO_PARAM_ROOT + "SPATIAL_SEND_PRIORITY"`
- `MIRO_PARAM_ROOT + "SPATIAL_SEND_OTHER"`
- `MIRO_PARAM_ROOT + "SPATIAL_NO_REAFF_COMPROMISE"`
- `MIRO_PARAM_ROOT + "SPATIAL_NO_SUPPRESS"`
- `MIRO_PARAM_ROOT + "SPATIAL_SHOW_COMPROMISE"`
- `MIRO_PARAM_ROOT + "SPATIAL_SHOW_TEST_PATTERN"`
- `MIRO_PARAM_ROOT + "TEST_ALARM"`


# Contacts
Luca Buoncompagni, EMAROlab, DIBRIS, University of Genoa.   
luca.buoncompagni@edu.unige.it
