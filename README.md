# ROS_Project
Hobby Projects on ROS


# ROS_Project


## Project 1

So my first project is very simple i.e ** "Hello, ROS" **

This was done referring to the book " A Gentle introduction to ROS"

Steps:-

First step is to create package name inside your ROS Directory

   catkin_create_pkg agitr #agitr is package name
This will create two configuration file package.xlm and cMakeList.txt

Writing Hello ROS program as in **src/agitr/hello.cpp **

Compiling the Hello program

Declaring dependencies

First, we need to declare the other packages on which ours program depends. For C++ programs, this step is needed primarily to ensure that catkin provides the C++ compiler with the appropriate flags to locate the header files and libraries that it needs. To list dependencies, edit the CMakeLists.txt in your package directory.

The default version of this file has this line:

     find_package(catkin REQUIRED)
Dependencies on other catkin packages can be added in a COMPONENTS section on this line:

     find_package(catkin REQUIRED COMPONENTS package-names)
For the hello example, we need one dependency on a package called roscpp , which provides the C++ ROS client library. The required find_package line, therefore, is:

     find_package(catkin REQUIRED COMPONENTS roscpp)
We should also list dependencies in the package manifest ( package.xml ), using the build_depend and run_depend elements:

   <build_depend>package-name</build_depend>
   <exec_depend>package-name</exec_depend>
In the example, the hello program needs roscpp both at build time and at run time, so the manifest should contain:

   <build_depend>roscpp</build_depend>
   <exec_depend>roscpp</exec_depend>
Declaring an executable

Next, we need to add two lines to CMakeLists.txt declaring the executable we would like to create. The general form is ~~~

         add_executable(executable-name source-files)
         target_link_libraries(executable-name ${catkin_LIBRARIES})
         
         ~~~
The first line declares the name of the executable we want, and a list of source files that should be combined to form that executable.

In this example, we want an executable called hello , compiled from a single source file called hello.cpp , so we would add these lines to CMakeLists.txt :

         ~~~
         
         add_executable(hello hello.cpp)
         target_link_libraries(hello ${catkin_LIBRARIES})
         
         # Specify locations of header files.
         include_directories(include ${catkin_INCLUDE_DIRS})
         
         ~~~
Building the workspace

Go in the directory of the ROS folder and use the command

       catkin_make
Sourcing setup.bash

      source devel/setup.bash
Executing the hello program

      rosrun agitr hello
Output:-

[ INFO] [1562914380.071525679]: Hello, ROS!
