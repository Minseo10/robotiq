# Getting Started

Temporary instructions for Robotiq 3F Adaptive Gripper and FT 300 Sensor

## 3-Finger Adaptive Gripper

Please refer to this [link](https://assets.robotiq.com/website-assets/support_documents/document/3-Finger_PDF_20201208.pdf?_ga=2.232222687.1180264451.1621211025-507727247.1615802140) for the detailed documentation.

### Network Setup

1. Open up the user bay and connect a network cable to your PC. 
You should give yourself an IP address in `192.168.1.X` space. 
Do not use **11**, as it is an address for the gripper. 
Below is an example of how to configure your network:

    |  Address           | Netmask         | Gateway         |
    |  :---------------: | :-------------: | :-------------: |
    |  192.168.1.*50*  |  255.255.255.0  |  192.168.1.1  |

2. Specify the ROS_IP and ROS_MASTER_URI. Add the lines in *~/.bashrc* file.
    ```sh
    export ROS_IP=192.168.1.22
    export ROS_MASTER_URI=http://$ROS_IP:11311
    ```

### Python Demo

Run the lines below in the respective terminals.
```sh
roscore
rosrun robotiq_3f_gripper_control Robotiq3FGripperTcpNode.py 192.168.1.11
rosrun robotiq_3f_gripper_control Robotiq3FGripperSimpleController.py
rosrun robotiq_3f_gripper_control Robotiq3FGripperStatusListener.py
```
You can try simple control with the keyboard input.

### Rviz Demo

Run the lines below in the respective terminals.
```sh
roscore
rosrun robotiq_3f_gripper_control Robotiq3FGripperTcpNode.py 192.168.1.11
rosrun robotiq_3f_gripper_joint_state_publisher robotiq_3f_gripper_joint_states
roslaunch robotiq_3f_gripper_visualization robotiq_gripper_upload.launch
```
You can try simple control with rviz panel, and visualize the gripper state.


## FT 300 Sensor

### Network Setup

No additional setup needs to be done.

### Rviz Demo

Run the lines below in the respective terminals.
```sh
roscore
roslaunch robotiq_ft_sensor visualize_ft300.launch
```
Add the *wrench stamped* topic.

