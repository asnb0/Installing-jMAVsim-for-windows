# ROS-Gazebo Bridge (ROS 2 Humble & Gazebo Harmonic)

This README explains how to set up and use the **ROS ↔ Gazebo (gz)** bridge on **Ubuntu 22.04** using  
**ROS 2 Humble** and **Gazebo Harmonic**.

---

## 1. Installation

Install the ROS–Gazebo bridge package:

```bash
sudo apt install ros-humble-ros-gzharmonic
```

This package provides a collection of tools and nodes that allow **ROS 2 topics, services, and actions** to communicate with **Gazebo transport messages** (gz.msgs).

---

## 2. What Is the ROS ↔ Gazebo Bridge?

The **ros_gz_bridge** node enables **bidirectional message passing** between ROS 2 and Gazebo.  
It allows topics from Gazebo (gz transport) to be exposed as ROS 2 topics — and vice versa — by translating message types between the two ecosystems.

### 📘 Official Documentation  
🔗 [ROS ↔ Gazebo Bridge (ros_gz_bridge)](https://docs.ros.org/en/rolling/p/ros_gz_bridge/)

note that you can get the mapping of the topics form this Documentation.

---

## 3. Understanding the Bridge Format

When launching a bridge between ROS 2 and Gazebo, the topic remapping uses this format:

```
ros2 run ros_gz_bridge parameter_bridge <topic_name>@<ros2_message_type>@<gz_message_type>
```

### Breakdown:
| Part | Description |
|------|--------------|
| `/world/baylands/model/x500_gimbal_0/link/camera_link/sensor/camera/image` | The **Gazebo topic path** for the camera image. |
| `sensor_msgs/msg/Image` | The **ROS 2 message type** used for images. |
| `gz.msgs.Image` | The **Gazebo message type** corresponding to the same data. |

This tells the bridge:  
> “Forward messages between Gazebo’s `/camera/image` topic (of type `gz.msgs.Image`) and a ROS 2 topic `/camera/image` (of type `sensor_msgs/msg/Image`).”

---

## 4. Running the Bridge

Run the bridge manually using the following command:
note that is for the camera of PX4 X500_gimbal model 
```bash
ros2 run ros_gz_bridge parameter_bridge /world/baylands/model/x500_gimbal_0/link/camera_link/sensor/camera/image@sensor_msgs/msg/Image@gz.msgs.Image
```
