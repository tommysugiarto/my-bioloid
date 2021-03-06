my-bioloid
==========

## rviz

Standalone (using TF transform from joint state publisher GUI):

    roslaunch bioloid_typea_description rviz.launch standalone:=true

With ros control (using TF from robot joint publisher's joint state from ros control boiler plate): 

    roslaunch bioloid_typea_description rviz.launch

## Simulator

If the robot fall when play is pressed, make sure the control are started:
 - install the library:

    sudo apt-get install ros-kinetic-gazebo-ros-control

 - make sure the namespace of the spawned controller manager and the libgazebo in urdf are matching

Start physics simulator (gazebosim):

    roslaunch bioloid_typea_gazebo gazebo.launch (python)
    roslaunch bioloid_motion gazebo.launch (C++)

Start the walking script:

    rosrun bioloid_typea_gazebo walker_demo.py (python)
    rosrun bioloid_motion robot_motion_walk_test (C++)

## Real robot

Control:

    sudo usermod -a -G dialout $USER (for usb2ax /dev/ttyACM0)
    roslaunch ros_control_boilerplate bioloid_hardware.launch

Walking demo:

    rosrun bioloid_typea_gazebo walker.py

    rosrun bioloid_typea_gazebo walker_demo.py

Camera (30fps):

    rosrun raspicam raspicam_node

Camera Host side:

    rosrun image_view image_view image:=/camera/image _image_transport:=compressed

IMU:

    rosrun navio ahrs

PS4 joystick:

    pair the DS4 joystick
    start daemon ds4drv --hidraw
    roslaunch teleop_twist_joy teleop.launch


