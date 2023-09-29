# Gazebo Harmonic Highlights

## New Features

- [Add support for writing systems in Python and provide Python bindings for gz-transport](https://github.com/gazebosim/gz-sim/pull/2081)
  - Gazebo now provides a way to write systems in Python. This is done using the `gz::sim::systems::PythonSystemLoader`
    system which loads a given python module specified by its `<module_name>` parameter. The module is expected to
    provide a function called `get_system` that returns an instance of a class that implements the various interfaces in
    `gz::sim::System`. In addition, it is now possible to use `gz-transport` to publish, subscribe or do service
    requests from Python (see also [gz-transport#411](https://github.com/gazebosim/gz-transport/pull/411) and
    [gz-msgs#362](https://github.com/gazebosim/gz-msgs/pull/362))

- [Automatically compute the Moment of Inertia of Meshes](https://github.com/gazebosim/gz-sim/pull/2061)
  - This feature enables automatic calculation for the Moments of Inertia, Mass, and Inertial Pose (Center of Mass pose)
    of a link described using SDFormat. Primitive shapes (Box, Capsule, Cylinder, Ellipsoid, Sphere) and water-tight
    triangle meshes are currently supported (see [tutorial](https://gazebosim.org/api/sim/8/auto_inertia_calculation.html) for other
    requirements). Using this feature, a user can easily set up an accurate simulation with physically plausible
    inertial values for a link. This also removes the dependency on manual calculations or 3rd-party mesh processing
    software which can help lower the barrier of entry for beginners.(see also
    [sdformat#1299](https://github.com/gazebosim/sdformat/pull/1299),
    [sdformat#1298](https://github.com/gazebosim/sdformat/pull/1298),
    [Proposal](http://sdformat.org/tutorials?tut=auto_inertial_params_proposal&cat=pose_semantics_docs&))

- [Add new MouseDrag plugin](https://github.com/gazebosim/gz-sim/pull/2038), and [gz-sim#2057](https://github.com/gazebosim/gz-sim/pull/2057)
  - This new plugin allows the user to exert forces and torques by dragging objects in the scene with the mouse cursor.
    The Gazebo-classic Apply Force and Torque GUI interface, which allows specifying exact forces and torques, has also
    been ported to Gazebo with some additional improvements ([see](https://github.com/gazebosim/gz-sim/pull/2014)).

- [Support fluid added mass](https://github.com/gazebosim/gz-sim/pull/1592)
  - Adds support for simulating the virtual mass of the displaced volume of objects that are moving through fluids. (See
    also [gz-physics#384](https://github.com/gazebosim/gz-physics/pull/384) [gz-physics#462](https://github.com/gazebosim/gz-physics/pull/462))

- [Add bullet-featherstone plugin](https://github.com/gazebosim/gz-physics/pull/373), [gz-physics#434](https://github.com/gazebosim/gz-physics/pull/434)
  - Adds support for Bullet's Featherstone implementation, which is a technique using a reduced coordinate
    representation of open kinematic chains. For simulations involving open kinematic chains, RTF performance may be
    better under this plugin.

- [Add interface to allow systems to declare parameters](https://github.com/gazebosim/gz-sim/pull/1431)
  - An interface that can be implemented by systems that allows them to declare parameters
    (`ISystemConfigureParameters`). Gazebo creates an instance of `ignition::transport::parameters::ParametersRegistry`
    (see [gz-transport#305](https://github.com/ignitionrobotics/gz-transport/pull/305)) with a namespace `/world/<world_name>` that
    provides the following services:
    - `/world/<world_name>/list_parameters` service: List available parameters names and types.
    - `/world/<world_name>/get_parameter` service: Get the type and value of a parameter.
    - `/world/<world_name>/set_parameter` service: Set a parameter: parameter name, value and type need to be provided.

- [Generate messages in downstream builds](https://github.com/gazebosim/gz-msgs/pull/339)
  - This re-works message generation both in the way that gz-msgs builds messages from protobuf definitions,
    as well as exports the functionality to downstream developers. Developers can now easily generate their
    own message definitions that are compatible with Gazebo tooling, such as msgs or transport.

- [Mimic constraint feature using bullet-featherstone](https://github.com/gazebosim/gz-physics/pull/517)
  - Adds a new joint actuation constraint called the Mimic constraint that enforces a linear relationship between
    the output position of two joint axes. This is serves as a better alternative to the Gearbox joint and provides more
    flexibility as it allows setting constraints on the output of prismatic joints and other joints with translational
    outputs. This feature is currently only available when using the Bullet-featherstone physics engine in Gazebo. (See
    [gz-sim#1838](https://github.com/gazebosim/gz-sim/pull/1838),
    [sdformat#1166](https://github.com/gazebosim/sdformat/pull/1166))

- [Add LensFlare](https://github.com/gazebosim/gz-sim/pull/1933)
  - Adds Lens Flare System that adds Lens Flare Render Pass to the camera and allows users to enable lens flare in
    camera images. The lens flares can be configured using `<scale>`, `<color>`, and `<occlusion_steps>` tags in the
    SDFormat file. This is supported in both Ogre and Ogre2 rendering engines and works with regular and wide angle
    cameras. (See [gz-rendering#775](https://github.com/gazebosim/gz-rendering/pull/775),
    [gz-rendering#752](https://github.com/gazebosim/gz-rendering/pull/752))

- [Global illumination VCT & CI VCT](https://github.com/gazebosim/gz-rendering/pull/675)
  - Adds Real Time Global Illumination on the GUI side based on one of these two techniques:
    1. VCT (Voxel Cone Tracing)
    2. CI VCT (Cascaded Image Voxel Cone Tracing). Requires Vulkan.
    A GUI plugin is provided for each Global illumination technique and offers a number of configurable parameters such as
    bounce count and voxel resolution that affect the quality of the resulting scene. Global illumination for camera sensors
    is not available yet.

- [Add Vulkan QML backend](https://github.com/gazebosim/gz-gui/pull/467)
  - Improves support for the Vulkan in the 3D rendering window in Gazebo GUI by adding native Vulkan backend using
    Qt's QML Vulkan Render Hardware Interface (RHI).
    For Qt versions >= 5.15.2, Gazebo is able to pass the Vulkan texture from Ogre to Qt and renders it onto the QQuickWindow (GPU -> GPU).
    For Qt versions < 5.15.2, a fallback method is used in which the Vulkan texture from Ogre is first transferred to the CPU then passed
    to Qt (GPU -> CPU -> GPU).

- [Add support for Acoustic comms](https://github.com/gazebosim/gz-sim/pull/1755), [gz-sim#1793](https://github.com/gazebosim/gz-sim/pull/1793)
  - Adds an acoustic comms system. The system contains a propagation model implemented where the signal to noise ratio
    is computed using sonar equation (as opposed to log path loss equation in RF comms propagation model) which in turn
    affects the packet drop probability.

- [Show subscribers info when running topic info](https://github.com/gazebosim/gz-transport/pull/384)
  - [List subscribed topics when running topic list](https://github.com/gazebosim/gz-transport/pull/379)
  - Adds the ability to list subscribers and show their info. Previously when using the `gz topic` CLI, only publishers are
    listed when `gz topic -l` or `gz topic -i -t <topic_name>` is invoked. Now it is possible to also see information
    about the subscribers.

- [Add support for merge-includes in worlds](https://github.com/gazebosim/sdformat/pull/1233)
  - Implements support for the `//world/include/@merge` SDF tag, i.e. `<include merge='true'>` in `<world>`.
    Merge-include in `<world>` allows models that themselves contain nested models to be merged into the world such that
    the nested models are placed directly in the `<world>` without the additional name scope of the parent model.

- [Support world joints (joints inside `<world>` tags)](https://github.com/gazebosim/gz-sim/pull/1949)
  - [dartsim: Add support for joints in worlds](https://github.com/gazebosim/gz-physics/pull/501)
  - [sdf/1.10: support //world/joint specification](https://github.com/gazebosim/sdformat/pull/1117)
  - Implements support for the `//world/joint` SDF tag that allows two models in `<world>` to be attached together by
    the specified joint. Note that some systems that operate on joints, such as the JointPositionController,
    require that the system is instantiated inside a model, and therefore, will not work with world joints.

- [Add Projector](https://github.com/gazebosim/gz-rendering/pull/845)
  - [Support loading Projectors](https://github.com/gazebosim/gz-sim/pull/1979)
  - [Add Projector DOM](https://github.com/gazebosim/sdformat/pull/1277)
  - Adds a projector feature that projects out a texture onto a surface. A projector can be attached to a link in sdf
    using the [`<projector>`](http://sdformat.org/spec?ver=1.10&elem=link#link_projector) sdf element. The feature is supported
    in both Ogre and Ogre2 rendering engines. One caveat with the Ogre2 implementation is that the projection
    is not in the form of a "frustum" (i.e. projection becomes larger at longer distance) but it's done using screen space decals.
    Think of it as a rectangular volume and any surface that intersects with the volume will have the texture mapped onto it.

- [Add Support for wide-angle cameras in ogre2](https://github.com/gazebosim/gz-rendering/pull/733)
  - Ports the wide angle camera implementation to the Ogre2 render engine. It supports the same
    [lens mapping functions](http://sdformat.org/spec?ver=1.10&elem=sensor#lens_type) that are available in
    Ogre the render engine. Lens flares are also supported.

- [Add DopplerVelocityLog sensor](https://github.com/gazebosim/gz-sensors/pull/290)
  - [Add DopplerVelocityLogSystem plugin](https://github.com/gazebosim/gz-sim/pull/1804)
  - Adds DopplerVelocityLog (DVL) sensor that produces velocity estimates of the vehicle. Two modes are available: bottom tracking
    and water mass tracking. With bottom tracking, the DVL sensor has multiple configurable acoustic beams pointing downwards at an angle
    to the seabed to measure distance and compute velocity as the vehicle moves over time. Water mass tracking can be used when
    seabed is not available or within range of the beams. This particular mode requires the EnvironmentPreload system to be loaded as well,
    which will parse and load water velocity data from a CSV file into the `EnvironmentalData` component.

- [Add airspeed sensor](https://github.com/gazebosim/gz-sensors/pull/305)
  - [Add airspeed sensor](https://github.com/gazebosim/gz-sim/pull/1847)
  - [Add Airspeed sensor](https://github.com/gazebosim/sdformat/pull/1215)
  - Adds air speed sensor that measures differential pressure (hPa) and temperature (kelvin) at a given altitude. Optional Gaussian noise
    model can be applied to the pressure data.

- [Add Reset button to world_control](https://github.com/gazebosim/gz-gui/pull/476)
  - Adds a reset button to the WorldControl GUI plugin which by default is located at the lower left corner of the Gazebo GUI window.
    When pressed, the plugin makes a request to the server to reset the simulation.

- [Allow loading a model SDF file in the Server class, and from the command line](https://github.com/gazebosim/gz-sim/pull/1775)
  - Adds support for `gz sim` to load a model SDF file (in addition to a world SDF file). The model is loaded into
    the default world. Specifically, this is done by updating the constructor of the Server class to handle SDF files
    that contain a `<model>` without a `<world>`.

- [Allow using a CSV file to define currents for hydrodynamic system](https://github.com/gazebosim/gz-sim/pull/1839)
  - [Add multichannel lookup for environment sensors.](https://github.com/gazebosim/gz-sim/pull/1814)
  - [Adds a tool for environment data visualization](https://github.com/gazebosim/gz-sim/pull/1748)
  - Extends the Hydrodynamic system to support reading water current data from a defined in a CSV file.
    This requires that The EnvironmentPreload system to be available in the world, which is used to parse and load
    the data in the CSV file into the `EnvironmentalData` component.

- [Include contact force, normal, and depth in contact message](https://github.com/gazebosim/gz-sim/pull/2050)
  - In addition to position data, the contact message published by a contact sensor now includes force, normal and
    depth data for each contact point.

- [Add support for adding cmake extras to packages in `gz-cmake`](https://github.com/gazebosim/gz-cmake/pull/345)
  - This feature gives library authors the ability to export and install additional CMake functionality.
  This is useful for providing macros/functions for downstream developers to use as part of their CMake scripts.

- [Add optional binary relocatability in all Gazebo libraries](https://github.com/gazebosim/gz-cmake/pull/334)
  - Optional CMake behavior to allow for the built installation to be relocated to a different directory
    at runtime. Enabled via `GZ_ENABLE_RELOCATABLE_INSTALL` CMake variable. This feature is heavily used
    in the conda distribution of the gazebo libraries.

- [Add CSV data parsing capability in `gz-common`](https://github.com/gazebosim/gz-common/pull/402)
  - Adds a common implementation of parsing CSV data files.

- [MecanumDriveOdometry to handle odometry estimation of Mecanum wheeled models](https://github.com/gazebosim/gz-math/pull/486)
  - Adds a math class to compute odometry estimation based on a set of kinematic properties and wheel speeds for
    Mecanum-drive vehicles.

- [Add support for bayer images to Ogre and Ogre2](https://github.com/gazebosim/gz-rendering/pull/838)
  - Extends camera sensors to support Bayer image formats. To use these formats, set the
    [`<format>`](http://sdformat.org/spec?ver=1.10&elem=sensor#image_format) sdf element to one of these strings:
    `BAYER_RGGB8`, `BAYER_BGGR8`, `BAYER_GBRG8`, `BAYER_GRBG8`. The `Image Display` GUI plugin in Gazebo has also been
    extended to support visualizing Bayer images.

- [Set custom camera projection values from SDFormat](https://github.com/gazebosim/gz-sensors/pull/314), also [gz-sensors#293](https://github.com/gazebosim/gz-sensors/pull/293), [gz-sensors#249](https://github.com/gazebosim/gz-sensors/pull/249)
  - [Update Camera Intrinsics in camera_info topic](https://github.com/gazebosim/gz-sensors/pull/281)
  - Allows users to set the projection matrix of a camera sensor via the
    [`<projection>`](http://sdformat.org/spec?ver=1.10&elem=sensor#lens_projection) sdf element.
    Similarly, if the lens [`<intrinsics>`](http://sdformat.org/spec?ver=1.10&elem=sensor#lens_intrinsics) parameters are specified,
    the camera sensor will use a custom projection matrix that is built from these values.

- [Add Camera Info topic support for cameras](https://github.com/gazebosim/gz-sensors/pull/285)
  - [Add camera info topic to Camera](https://github.com/gazebosim/sdformat/pull/1198)
  - Adds support for configuring the camera info topic via the `<camera_info_topic>` SDF parameter inside `<camera>`.

- [Add support for 16 bit image format](https://github.com/gazebosim/gz-sensors/pull/276)
  - Extends camera sensors to support 16 bit grayscale image format. To use this format, set the [`<format>`](http://sdformat.org/spec?ver=1.10&elem=sensor#image_format) sdf element to `L_INT16`.

- [Add optional optical frame id to camera sensors](https://github.com/gazebosim/gz-sensors/pull/259)
  - Extends CameraSensor and RGBDCameraSensor to parse the optional `<optical_frame_id>` SDF parameter.
    If the parameter is specified, the published sensor messages will now have their `frame_id` in the message
    header set to the specified value.

- [Add more convenience classes (Light, Actor, Sensor](https://github.com/gazebosim/gz-sim/pull/1918), [gz-sim#1913](https://github.com/gazebosim/gz-sim/pull/1913), [gz-sim#1912](https://github.com/gazebosim/gz-sim/pull/1912), [gz-sim#1910](https://github.com/gazebosim/gz-sim/pull/1910)
  - [Adds Python bindings for convenience class (Actor, Joint, Link, Model, Sensor, World)](https://github.com/gazebosim/gz-sim/pull/2043)
  - Adds convenience classes that abstract the Entity-Component-System (ECS) architecture and provide more user-friendly APIs are similar to
    those found in Gazebo-classic.

- [Allow re-attaching detached joint](https://github.com/gazebosim/gz-sim/pull/1687)
  - Extends the DetachableJoint system to support reattaching joints. The system now offers an topic that allows users to
    publish an empty message reattach the child link back to the parent link using a fixed joint.
    The topic name can be configured using the `<attach_topic>` parameter in SDF.

- [Allow specifying initial simulation time with a CLI argument](https://github.com/gazebosim/gz-sim/pull/1801)
  - Adds an optional command line argument, `initial-sim-time`, to `gz sim` for setting the initial value of the simulation time.
    Usage: `gz sim --initial-sim-time [t]`, where `[t]` is the time in seconds (floating point value)
    at which the simulation time will be set to when the simulator is started.

- [Add SensorTopic component to rendering sensors](https://github.com/gazebosim/gz-sim/pull/1908)
  - Add a `SensorTopic` component that stores the name of the sensor topic. This allows retrieval of the sensor topic string
    that is either specified via the `<topic>` sdf element or dynamically generated by Gazebo if no `<topic>` is specified.

- [Add thrust coefficient calculation](https://github.com/gazebosim/gz-sim/pull/1652)
  - Extends the Thruster system to support new parameters: `<wake_fraction>`, `<alpha_1>`, `<alpha_2>`. When specified,
    these parameters are used together with the vehicle linear velocity to compute the thrust coefficient
    based on Fossen's equations described in "Guidance and Control of Ocean Vehicles".

- [Add magnetometer value based on location](https://github.com/gazebosim/gz-sim/pull/1907)
  - Extends the Magnetometer system to support computing the magnetic field based on the sensor's location
    (spherical coordinates). The lat/lon coordinates index into lookup tables for Earth's magnetic field declination (deg),
    inclination (deg) and strength (centi-Tesla) that are used to compute the sensor's world magnetic field value.

- [JointPositionController: support nested joints](https://github.com/gazebosim/gz-sim/pull/1851)
  - Extends the Joint Position Controller system to support controlling nested joints (joints in nested models)
    by looking up joints using scoped names in addition to unscoped names. Users can now specify scoped names using the
   `<joint_name>` SDF param in the Joint Position Controller system, i.e. `model_name::joint_name`.

- [Add a utility for spawning subprocesses](https://github.com/gazebosim/gz-utils/pull/98)
  - Refactors common functionality for spawning executables into the utils package.
- [Update function to use sdf::Errors output instead of printing to the console](https://github.com/gazebosim/sdformat/issues/820)
- [Port embedSdf script from Ruby to Python3](https://github.com/gazebosim/sdformat/pull/884)
  - Ports remaining Ruby build-dependencies into Python. SDFormat now has no build dependency on Ruby.

## Bug Fixes

- [Speed up Resource Spawner load time by fetching model list asynchronously](https://github.com/gazebosim/gz-sim/pull/1962)
  - The Resource Spawner used to take a long time to load because it tried to fetch the list of all available models on Fuel instead of just the selected owner. And it did so while blocking the Qt thread, so the user was unable to interact with the GUI while the model list was being fetched. Now, the Resource Spawner only fetches the list of models for the default owner ("openrobotics") and allow users to add/remove any owner they want. The fetching is also done in a separate thread so as to not block the GUI. As part of this fix, the `gz-fuel-tools` iterator API
    has been fixed to properly [paginate REST requests](https://github.com/gazebosim/gz-fuel-tools/pull/350).

## Breaking Changes

- [Remove support for fuel.ignitionrobotics.org in SDFormat files](https://github.com/gazebosim/gz-fuel-tools/pull/293)

## Documentation

- [Add ROS 2 Integration Tutorials](https://github.com/gazebosim/docs/pull/371)
- [Add more tutorials on migrating from gazebo classic](https://github.com/gazebosim/gz-sim/pull/1930), [gz-sim#1929](https://github.com/gazebosim/gz-sim/pull/1929), [gz-sim#1925](https://github.com/gazebosim/gz-sim/pull/1925), [gz-sim#1931](https://github.com/gazebosim/gz-sim/pull/1931)
- [Add rrbot example setup & update readme](https://github.com/gazebosim/ros_gz_project_template/pull/9)

