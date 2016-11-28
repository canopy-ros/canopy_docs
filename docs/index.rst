.. canopy_docs documentation master file, created by
   sphinx-quickstart on Sun Nov 27 23:15:53 2016.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to Canopy!
=======================================

Canopy, a cloud robotics framework for robots running ROS (Robot Operating System). The project aims to allow robots anywhere in the world to communicate with each other through the cloud, by providing a framework for multiple robots and computers, each running their own ROS master, to send messages to each other over the cloud. Canopy integrates seamlessly into the ROS framework; topics published to on one robot are automatically sent over a websocket and republished on another robot, as if they were on the same network. The user simply needs to create a Canopy client node, list the topics to be sent, and optionally select which other robots are allowed to receive each topic.

Canopy consists of a server stack and a client ROS package. The server acts as the central hub for all communication.

The code for both the server stack and client package are open source, and are available on `GitHub <https://github.com/canopy-ros>`_.

.. toctree::
   :maxdepth: 2
   :glob:
   :caption: User Documentation

   client-docs
   server-docs
