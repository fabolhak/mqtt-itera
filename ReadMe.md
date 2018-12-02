# MQTT-ROS Bridge Test

This are some example config and launch files for the [MQTT-ROS Bridge](https://github.com/groove-x/mqtt_bridge) package from groove-x for testing purposes only.

## Install

`sudo apt install ros-<distro>-mqtt-bridge`

## Use Case

I tried to interface the Iteratec [TRAZE](https://traze.iteratec.de/) game via ROS. However, this was only partly successfull. The biggest problem I had was the use of array definitions without a property name in JSON. This data structure can not be modelled with a ROS message in a straight forward fashion. For example I was not able to convert the following (valid) JSON message into a ROS message:

```json
[3.3, 5.5, 6.6]
```

Instead the following message works:

```json
{
   "test":[3.3, 5.5, 6.6]
}
```

```text
float32[] test
```

However, I didn't spend to much time on it. Maybe it is possible to extend the [rosbridge_library](https://github.com/RobotWebTools/rosbridge_suite/blob/master/rosbridge_library/src/rosbridge_library/internal/message_conversion.py) somehow to get it working.