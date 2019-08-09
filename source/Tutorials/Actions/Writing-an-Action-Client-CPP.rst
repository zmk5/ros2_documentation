Writing an Action Client (C++)
==============================

Setting up the package
------------------

Before creating out C++ Action Client, we must first set up our package. First, navigate to the directory you created earlier
during the prerequisite:

.. code-block:: bash

    # Change to the root of the workspace (ie. action_ws)
    cd ~/action_ws
    cd action_tutorials

Let's then create our new package for the C++ Action Client:

.. code-block:: bash

    # Create a ros2 package
    ros2 pkg create action_tutorials_cpp

We should first add the required dependencies to our ``package.xml``:

.. code-block:: xml

    <depend>action_tutorials_interfaces</depend>
  	<depend>rclcpp</depend>
  	<depend>rclcpp_action</depend>
  	<depend>rclcpp_components</depend>

We then should set up our dependencies in out ``CMakeLists.txt``:

.. code-block:: cmake

    find_package(action_tutorials_interfaces REQUIRED)
    find_package(rclcpp REQUIRED)
    find_package(rclcpp_action REQUIRED)
    find_package(rclcpp_components REQUIRED)

Now that we have our dependencies setup, we can start writing our C++ action client

Title here
------------------

Navigate to the ``src`` directory and create a file ``fibonacci_action_client.cpp`` and add the following boilerplate code:

.. literalinclude:: client_0.c++
    :language: c++


