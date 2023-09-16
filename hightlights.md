## gazebosim/docs:
- [Add ROS 2 Integration Tutorials](https://github.com/gazebosim/docs/pull/371)

## gazebosim/gz-cmake:
- [Add support for adding cmake extras to packages](https://github.com/gazebosim/gz-cmake/pull/345)
- [Add optional binary relocatability in downstream libraries](https://github.com/gazebosim/gz-cmake/pull/334)

## gazebosim/gz-common:
- [Add CSV data parsing](https://github.com/gazebosim/gz-common/pull/402)

## gazebosim/gz-fuel-tools:
- [Reflect pagination of RESTful requests in iterator API ](https://github.com/gazebosim/gz-fuel-tools/pull/350)
- [Remove support for fuel.ignitionrobotics.org in SDFormat files](https://github.com/gazebosim/gz-fuel-tools/pull/293)

## gazebosim/gz-gui:
- [Add Camera FPS plugin](https://github.com/gazebosim/gz-gui/pull/523)
- [Add Vulkan QML backend](https://github.com/gazebosim/gz-gui/pull/467)
- [Add Reset button to world_control](https://github.com/gazebosim/gz-gui/pull/476)

## gazebosim/gz-math:
- [MecanumDriveOdometry to handle odometry estimation of Mecanum wheeled models](https://github.com/gazebosim/gz-math/pull/486)

## gazebosim/gz-msgs:
- [Add Python message generation](https://github.com/gazebosim/gz-msgs/pull/362)
- [Generate messages in downstream builds](https://github.com/gazebosim/gz-msgs/pull/339)

## gazebosim/gz-physics:
- [Mimic constraint feature using bullet-featherstone](https://github.com/gazebosim/gz-physics/pull/517)
- [dartsim: Add support for joints in worlds](https://github.com/gazebosim/gz-physics/pull/501)
- [Support fluid added mass](https://github.com/gazebosim/gz-physics/pull/384), [gz-physics#462](https://github.com/gazebosim/gz-physics/pull/462)
- [Add bullet-featherstone plugin](https://github.com/gazebosim/gz-physics/pull/373), [gz-physics#434](https://github.com/gazebosim/gz-physics/pull/434)

## gazebosim/gz-rendering:
- [Add Projector](https://github.com/gazebosim/gz-rendering/pull/845)
- [Add Support for wide-angle cameras in ogre2](https://github.com/gazebosim/gz-rendering/pull/733)
- [Add support for bayer images to Ogre and Ogre2](https://github.com/gazebosim/gz-rendering/pull/838)
- [Add LensFlare](https://github.com/gazebosim/gz-rendering/pull/775), [gz-rendering#752](https://github.com/gazebosim/gz-rendering/pull/752)
- [Global illumination VCT & CI VCT](https://github.com/gazebosim/gz-rendering/pull/675)

## gazebosim/gz-sensors:
- [Add trigger to BoundingBoxCamera](https://github.com/gazebosim/gz-sensors/pull/322)
- [Set custom projection values from SDFormat](https://github.com/gazebosim/gz-sensors/pull/314), also [gz-sensors#293](https://github.com/gazebosim/gz-sensors/pull/293), [gz-sensors#249](https://github.com/gazebosim/gz-sensors/pull/249)
- [Add Camera Info topic support for cameras](https://github.com/gazebosim/gz-sensors/pull/285)
- [Add airspeed sensor](https://github.com/gazebosim/gz-sensors/pull/305)
- [Add DopplerVelocityLog sensor](https://github.com/gazebosim/gz-sensors/pull/290)
- [Update Camera Intrinsics in camera_info topic](https://github.com/gazebosim/gz-sensors/pull/281)
- [Add support for 16 bit image format](https://github.com/gazebosim/gz-sensors/pull/276)
- [Add optional optical frame id to camera sensors](https://github.com/gazebosim/gz-sensors/pull/259)

## gazebosim/gz-sim:
- [Add new MouseDrag plugin](https://github.com/gazebosim/gz-sim/pull/2038), and [gz-sim#2057](https://github.com/gazebosim/gz-sim/pull/2057)
- [Apply Force and Torque GUI plugin](https://github.com/gazebosim/gz-sim/pull/2014), [gz-sim#2026](https://github.com/gazebosim/gz-sim/pull/2026), [gz-sim#2056](https://github.com/gazebosim/gz-sim/pull/2056), [gz-sim#2051](https://github.com/gazebosim/gz-sim/pull/2051)
- [Add support for writing systems in Python](https://github.com/gazebosim/gz-sim/pull/2081)
- [Adds Python bindings for convenience class (Actor, Joint, Link, Model, Sensor, World](https://github.com/gazebosim/gz-sim/pull/2043), [gz-sim#2040](https://github.com/gazebosim/gz-sim/pull/2040), [gz-sim#2041](https://github.com/gazebosim/gz-sim/pull/2041), [gz-sim#2042](https://github.com/gazebosim/gz-sim/pull/2042), [gz-sim#2039](https://github.com/gazebosim/gz-sim/pull/2039), [gz-sim#2036](https://github.com/gazebosim/gz-sim/pull/2036), [gz-sim#2035](https://github.com/gazebosim/gz-sim/pull/2035)
- [Include contact force, normal, and depth in contact message](https://github.com/gazebosim/gz-sim/pull/2050)
- [Add support for mimic joints (only available with bullet-featherstone physics engine)](https://github.com/gazebosim/gz-sim/pull/1838)
- [Automatically compute the Moment of Inertia of Meshes](https://github.com/gazebosim/gz-sim/pull/2061)
- [Support world joints (joints inside `<world>` tags)](https://github.com/gazebosim/gz-sim/pull/1949)
- [Support loading Projectors](https://github.com/gazebosim/gz-sim/pull/1979)
- [Speed up Resource Spawner load time by fetching model list asynchronously](https://github.com/gazebosim/gz-sim/pull/1962)
- [Allow re-attaching detached joint](https://github.com/gazebosim/gz-sim/pull/1687)
- [Add more tutorials on migrating from gazebo classic](https://github.com/gazebosim/gz-sim/pull/1930), [gz-sim#1929](https://github.com/gazebosim/gz-sim/pull/1929), [gz-sim#1925](https://github.com/gazebosim/gz-sim/pull/1925), [gz-sim#1931](https://github.com/gazebosim/gz-sim/pull/1931)
- [Add DopplerVelocityLogSystem plugin](https://github.com/gazebosim/gz-sim/pull/1804)
- [Add more convenience classes (Light, Actor, Sensor](https://github.com/gazebosim/gz-sim/pull/1918), [gz-sim#1913](https://github.com/gazebosim/gz-sim/pull/1913), [gz-sim#1912](https://github.com/gazebosim/gz-sim/pull/1912), [gz-sim#1910](https://github.com/gazebosim/gz-sim/pull/1910)
- [Allow specifying initial simulation time with a CLI argument](https://github.com/gazebosim/gz-sim/pull/1801)
- [Add SensorTopic component to rendering sensors](https://github.com/gazebosim/gz-sim/pull/1908)
- [Add Lens Flare System](https://github.com/gazebosim/gz-sim/pull/1933)
- [Fluid added mass](https://github.com/gazebosim/gz-sim/pull/1592)
- [Add airspeed sensor](https://github.com/gazebosim/gz-sim/pull/1847)
- [Allow using a CSV file to define currents for hydrodynamic system](https://github.com/gazebosim/gz-sim/pull/1839)
- [Add multichannel lookup for environment sensors.](https://github.com/gazebosim/gz-sim/pull/1814)
- [GUI for Global Illumination (VCT / CI VCT)](https://github.com/gazebosim/gz-sim/pull/1597)
- [Add interface to allow systems to declare parameters](https://github.com/gazebosim/gz-sim/pull/1431)
- [Allow loading a model SDF file in the Server class, and from the command line](https://github.com/gazebosim/gz-sim/pull/1775)
- [Adds a tool for environment data visualization](https://github.com/gazebosim/gz-sim/pull/1748)
- [Add support for Acoustic comms](https://github.com/gazebosim/gz-sim/pull/1755), [gz-sim#1793](https://github.com/gazebosim/gz-sim/pull/1793)
- [Adding thrust coefficient calculation](https://github.com/gazebosim/gz-sim/pull/1652)
- [Add magnetometer value based on location](https://github.com/gazebosim/gz-sim/pull/1907)
- [JointPosController: support nested joints](https://github.com/gazebosim/gz-sim/pull/1851)

## gazebosim/gz-transport:
- [Python Bindings for Publisher, Subscriber and Service Request features.](https://github.com/gazebosim/gz-transport/pull/411)
- [Show subscribers info when running topic info](https://github.com/gazebosim/gz-transport/pull/384)
- [List subscribed topics when running topic list](https://github.com/gazebosim/gz-transport/pull/379)
- [Add parameters component](https://github.com/gazebosim/gz-transport/pull/305)

## gazebosim/gz-utils:
- [Add a utility for spawning subprocesses](https://github.com/gazebosim/gz-utils/pull/98)

## gazebosim/ros_gz_project_template:
- [Add rrbot example setup & update readme](https://github.com/gazebosim/ros_gz_project_template/pull/9)

## gazebosim/sdformat:
- [New specification version 1.11](https://github.com/gazebosim/sdformat/pull/1298)
- [Update function to use sdf::Errors output instead of printing to the console](https://github.com/gazebosim/sdformat/pull/1294), [sdformat#1153](https://github.com/gazebosim/sdformat/pull/1153), [sdformat#1164](https://github.com/gazebosim/sdformat/pull/1164), [sdformat#1163](https://github.com/gazebosim/sdformat/pull/1163), [sdformat#1162](https://github.com/gazebosim/sdformat/pull/1162), [sdformat#1161](https://github.com/gazebosim/sdformat/pull/1161), [sdformat#1160](https://github.com/gazebosim/sdformat/pull/1160), [sdformat#1159](https://github.com/gazebosim/sdformat/pull/1159), [sdformat#1158](https://github.com/gazebosim/sdformat/pull/1158), [sdformat#1157](https://github.com/gazebosim/sdformat/pull/1157), [sdformat#1156](https://github.com/gazebosim/sdformat/pull/1156), [sdformat#1155](https://github.com/gazebosim/sdformat/pull/1155), [sdformat#1154](https://github.com/gazebosim/sdformat/pull/1154), [sdformat#1145](https://github.com/gazebosim/sdformat/pull/1145), [sdformat#1151](https://github.com/gazebosim/sdformat/pull/1151), [sdformat#1144](https://github.com/gazebosim/sdformat/pull/1144), [sdformat#1141](https://github.com/gazebosim/sdformat/pull/1141), [sdformat#1152](https://github.com/gazebosim/sdformat/pull/1152), [sdformat#1140](https://github.com/gazebosim/sdformat/pull/1140), [sdformat#1138](https://github.com/gazebosim/sdformat/pull/1138), [sdformat#1135](https://github.com/gazebosim/sdformat/pull/1135), [sdformat#1123](https://github.com/gazebosim/sdformat/pull/1123), [sdformat#1122](https://github.com/gazebosim/sdformat/pull/1122)
- [Joint axis mimic constraints: add `sdf` element](https://github.com/gazebosim/sdformat/pull/1166)
- [Automatic Moment of Inertia Calculations](https://github.com/gazebosim/sdformat/pull/1299), [sdformat#1304](https://github.com/gazebosim/sdformat/pull/1304), [sdformat#1299](https://github.com/gazebosim/sdformat/pull/1299), [sdformat#1304](https://github.com/gazebosim/sdformat/pull/1304), [sdformat#1317](https://github.com/gazebosim/sdformat/pull/1317)
- [Add Projector DOM](https://github.com/gazebosim/sdformat/pull/1277)
- [Add Airspeed sensor](https://github.com/gazebosim/sdformat/pull/1215)
- [Add support for merge-includes in worlds](https://github.com/gazebosim/sdformat/pull/1233)
- [Port embedSdf script from Ruby to Python3](https://github.com/gazebosim/sdformat/pull/884)
- [Add camera info topic to Camera](https://github.com/gazebosim/sdformat/pull/1198)
- [sdf/1.10: support //world/joint specification](https://github.com/gazebosim/sdformat/pull/1117)
