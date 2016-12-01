Client Documentation
====================

This page will help you set up the Canopy client so you can connect to an existing Canopy server. You will need to have ROS already installed.

Installation
------------

```bash
$ cd <YOUR CATKIN WORKSPACE>/src
$ git clone https://github.com/baalexander/rospy_message_converter
$ git clone https://github.com/canopy-ros/canopy_client
$ cd ..
$ catkin_make
```

Execution
---------

You will need to start the Canopy client node through a launch file. Here is an example.

```xml
<node pkg="canopy_client" type="client_node.py" name="node_name" output="screen">
    <param name="name" value="robot_name"/>
    <param name="host" value="canopy-server-example.com"/>
    <param name="port" value="8080"/>
    <param name="private_key" value="private_key" />
    <param name="description" value="example robot" />
    <rosparam>
        publishing:
            - /topic1
            - /topic2
        types:
            - geometry_msgs/Point
            - std_msgs/String
        trusted:
            - ".*"
            - other1 other2
    </rosparam>
</node>
```

| Parameter    | Description                                                                                                                                                                                                                                                                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| name         | name that the robot will appear as on the network. Messages published over Canopy appear on other robots under the topic `robot_name/topicname`                                                                                                                                                                                                                               |
| host         | URL of the Canopy server                                                                                                                                                                                                                                                                                                                                                      |
| port         | port of the Canopy server                                                                                                                                                                                                                                                                                                                                                     |
| private_key  | used to isolate groups of robots sharing the same server. Ensure that all robots on the desired communication network have the same private key. If you would like to use the dashboard to view data in real time and use the Platform-as-a-service system, you will need to go to `canopy-server-example.com:3000` and create an account, which will generate a private key. |
| description  | contains a short text description of the robot                                                                                                                                                                                                                                                                                                                                |
| publishing   | list of topic names                                                                                                                                                                                                                                                                                                                                                           |
| types        | contains the message types for each topic, in the same order as above                                                                                                                                                                                                                                                                                                         |
| trusted      | allows you to specify which other robots should be able to receive messages from a published topic. Each item in the list corresponds to one topic and should be a space-separated list of regular expressions                                                                                                                                                                |
