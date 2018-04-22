# tracetools

The tracetools library is an Open Source project that provides tracing 
functions for message-passing middleware, specifically ROS.  

## Intended use 

The intended use of this software is for collecting data from robotic systems
*during development*.

The software is not targeted at use during production and has not been tested
for this purpose. However, the license conditions of the applicable Open Source
licenses allow you to adapt the software to your needs. Before using it in a
safety relevant setting, make sure that the software fulfills your requirements
and adjust it according to any applicable safety standards. 

## Instructions for use 

This is a regular catkin package and can just be dropped into your workspace as-is.

Then either call the ros::trace methods directly, or use our modified ros_comm version.

*However*, to actually generate tracing output, you need to 
 
1. Install LTTNG using (example for Ubuntu)
 	$ sudo apt install liblttng-ust-dev lttng-tools lttng-modules-dkms
2. Pass WITH_LTTNG (example for catkin tools)
	$ catkin config -DWITH_LTTNG=ON
3. Recompile your workspace
4. TEST tracing with the included test script
	$ rosrun tracetools tracetools_test
  In this case, "no news is good news". If a problem occurs, the script will
  let you know.
  

At runtime, LTTng is not active by default (so you can leave it in
your programs with no impact). To collect trace data, you need to
start an LTTng session. In this package, in 
[setup-lttng-roscpp.sh](scripts/setup-lttng-roscpp.sh), a simple 
configuration script is included.

For even easier usage, with automatic data conversion, check out the
[tracetools_analysis](https://github.com/bosch-robotics-cr/tracetools_analysis)
package. It provides a Python API for easy definition, execution and
analysis of tracing experiments.

## License 

This package is open-sourced under the Apache-2.0 license. See the 
[LICENSE](LICENSE) file for details. 

For a list of other open source components included in this package, see the 
file [3rd-party-licenses.txt](3rd-party-licenses.txt).

