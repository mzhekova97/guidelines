# ROS Tools

* [catkin_tools](https://catkin-tools.readthedocs.io/en/latest/): A Python package that provides command line tools for working with the catkin meta-buildsystem and catkin workspaces. These tools are separate from the Catkin CMake macros used in Catkin source packages. We recommend the utilization of `catkin_tools` instead of the `catkin_*` commands.

* [vcs_tool](http://wiki.ros.org/vcstool): Command-line tools for maintaining a workspace containing multiple versioned projects. All of our projects will always provide a `rosinstall` file. We, therefore, strongly encourage the utilization of `vcs_tool` for fetching and managing the packages.

