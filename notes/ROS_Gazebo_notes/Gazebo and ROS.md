# what is gazebo

Gazebo is an independent framework, so what you saw above is the stand-alone version of this program. Since our main framework for robotics development will be ROS, we need to learn how to use Gazebo’s plugins (which we discussed earlier in this tutorial) so that you can access the Gazebo functionality when you’re working with ROS.

There are six types of plugins in Gazebo:

    World
    Model
    Sensor
    System
    Visual
    GUI

Official link <http://gazebosim.org/tutorials?tut=plugins_hello_world&cat=write_plugin>

## creating plugin cc file

```cpp
// Includes a core set of basic Gazebo functions
#include <gazebo/gazebo.hh>
 
// All plugins must be in the gazebo namespace
namespace gazebo
{
  // Each plugin has to inherit from a plugin type.
  // In this case, we are inheriting from the WorldPlugin type.
  class WorldPluginTutorial : public WorldPlugin
  {
    public: WorldPluginTutorial() : WorldPlugin()
            {
              printf("Hello World!\n");
            }
 
    // This function is mandatory. It receives an element in 
    // Simulation Description Format (SDF) that contains the elements
    // and attributes that are specified in the loaded SDF file.
    public: void Load(physics::WorldPtr _world, sdf::ElementPtr _sdf)
            {
            }
  };
  // Register the plugin with the simulator.
  // Note that there are matching register macros for the six types
  // of plugins in Gazebo.
  GZ_REGISTER_WORLD_PLUGIN(WorldPluginTutorial)
}
```

## add to the CMakeLists.txt in gazebo pluging

```CMake
cmake_minimum_required(VERSION 2.8 FATAL_ERROR)
 
find_package(gazebo REQUIRED)
include_directories(${GAZEBO_INCLUDE_DIRS})
link_directories(${GAZEBO_LIBRARY_DIRS})
list(APPEND CMAKE_CXX_FLAGS "${GAZEBO_CXX_FLAGS}")
 
add_library(hello_world SHARED hello_world.cc)
target_link_libraries(hello_world ${GAZEBO_LIBRARIES})
 
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${GAZEBO_CXX_FLAGS}")
```

## compileing

Create a new directory called build.

    mkdir ~/gazebo_plugin_tutorial/build

    cd ~/gazebo_plugin_tutorial/build

Compile the code:

    cmake ../
    make

## plugin path

Now, add your library path to the GAZEBO_PLUGIN_PATH:

    export GAZEBO_PLUGIN_PATH=${GAZEBO_PLUGIN_PATH}:~/gazebo_plugin_tutorial/build

## Using plugins

Let’s create the SDF file.

Type the following command to open up a new file:

    code ~/gazebo_plugin_tutorial/hello.world

Add the following code:

```xml
<?xml version="1.0"?>
<sdf version="1.4">
  <world name="default">
    <plugin name="hello_world" filename="libhello_world.so"/>
  </world>
</sdf>
```

### use command 

    gzserver ~/gazebo_plugin_tutorial/hello.world --verbose

```
```