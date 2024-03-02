# tello_ros2_teleop_twist_keyboard
a custom Keyboard Teleoperation for ROS with the tello drone 


## Run

```sh
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```

Publishing to a different topic (in this case `my_cmd_vel`).
```sh
ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args --remap cmd_vel:=my_cmd_vel
```

## Usage

```
This node takes keypresses from the keyboard and publishes them as Twist
messages. It works best with a US keyboard layout.
---------------------------
Moving around:
   u    i    o
   j    k    l
   m    ,    .

For Holonomic mode (strafing), hold down the shift key:
---------------------------
   U    I    O
   J    K    L
   M    <    >

t : up (+z)
b : down (-z)

anything else : stop

q/z : increase/decrease max speeds by 10%
w/x : increase/decrease only linear speed by 10%
e/c : increase/decrease only angular speed by 10%

1: takeoff
2: land
3: emergency
4: flip left
5: flip right
6: flip front
7: flip back

CTRL-C to quit
```

## Parameters
- `stamped (bool, default: false)`
  - If false (the default), publish a `geometry_msgs/msg/Twist` message.  If true, publish a `geometry_msgs/msg/TwistStamped` message.
- `frame_id (string, default: '')`
  - When `stamped` is true, the frame_id to use when publishing the `geometry_msgs/msg/TwistStamped` message.
