# pupil_ros

How to install

Install pupil capture
https://docs.pupil-labs.com/ 

Install pip
>sudo apt-get install python-pip
>sudo pip install --upgrade pip

Install zmq 
> sudo pip install pyzmq

Install sox
> sudo apt-get install sox

Place the folder pupil_ros to your catkin workspace, and build the ROS package.
> cd Path/To/catkin_ws
> catkin_make
> source devel/setup.bash


This will build six custom ROS messages: pupil, pupil_positions, gaze, gaze_positions, surface_position, accu

How to run
1. Make pupil_zmq_ros_pub.py executable:
> cd catkin_ws/src/pupil_ros/scripts

> chmod +x pupil_zmq_ros_pub.py main_run_v4.py audio_output.py start_pupil.py
2. Launch ROS package:
> roslaunch pupil_ros pupil_ros.launch
3. Load plugin Pupil_Remote and Frame_Publisher
4. set localhost to 50010 in pupil remote
5. set frame publisher to bgr

How to subtract accuracy data
1. Setup rosbag record 
> rosbag record matcher/gaze_accu
2. Quit recording when ready
3. Make csv file with custom BAGFILE_NAME and LOGFILE_NAME (or logfile.txt)
> rostopic echo -b BAGFILE_NAME.bag -p /matcher/gaze_accu > LOGFILE_NAME.csv




