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

Let's go over the code skeleton and make sure we're setup and ready for writing the client.

1. For the include statements, we first need to include ``action_tutorials_interfaces/action/fibonacci.hpp`` so that we can use the action we defined earlier.
2. We must import ``rclcpp_action.hpp`` and ``register_node_macro.hpp`` from ``rclcpp_action`` and ``rclcpp_components``. We need ``rclcpp_action`` so that we can both send an ``action_goal`` to our server and recieve feedback. We need ``rclcpp_components`` in order to make our node/class a component.
3. In our class, ``fibonacci_action_client``, which inherits from ``Node``, we have a constructor which has has one argument, taking ``NodeOptions``. 
4. The ``send_goal`` function sends the goal to the server and sets up callbacks for the initial response, the feedback throughout, and the final result from the server.
5. We have two private member variables, ``client_ptr_`` and ``timer_``. ``timer_`` is used to send the action goal to the server with a certain time interval. ``client_ptr_`` creates the action client and send the goal to the server.
6. Finally, we have our three callback functions – one for intial response, one for feedback, and one for the final result.
7. On L50, we call a macro ``RCLCPP_COMPONENTS_REGISTER_NODE`` to register the plugin name, ``action_tutorials_cpp::FibonacciActionClient`` , with the ament resource index.

Now we will start writing out functions and get our client up and running

