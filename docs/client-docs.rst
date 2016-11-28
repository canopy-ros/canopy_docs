Client Documentation
====================

This page will help you set up the Canopy client so you can connect to an existing Canopy server. You will need to have ROS already installed.

Installation
------------

1. Clone the repository at `https://github.com/baalexander/rospy_message_converter <https://github.com/baalexander/rospy_message_converter>`_ into your catkin workspace.
2. Clone the repository at `https://github.com/canopy-ros/canopy_client <https://github.com/canopy-ros/canopy_client>`_ into your catkin workspace.
3. Run ``catkin_make`` to install both packages.

Execution
---------

You will need to start the Canopy client node through a launch file. Here is an example.

.. code-block:: xml

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

The "name" parameter is the name that the robot will appear as on the network. Messages published over Canopy appear on other robots under the topic `robot_name/topicname`.

The "host" parameter is the URL of the Canopy server.

The "port" parameter is the port of the Canopy server.

The "private_key" parameter is used to isolate groups of robots sharing the same server. Ensure that all robots on the desired communication network have the same private key. If you would like to use the dashboard to view data in real time and use the Platform-as-a-service system, you will need to go to `canopy-server-example.com:3000` and create an account, which will generate a private key.

The "description" parameter contains a short text description of the robot.

The parameters under ``<rosparam>`` specify which topics the Canopy client node should publish over the network.

The "publishing" list is the list of topic names.

The "types" list contains the message types for each topic, in the same order as above.

The "trusted" list allows you to specify which other robots should be able to receive messages from a published topic. Each item in the list corresponds to one topic and should be a space-separated list of regular expressions.
