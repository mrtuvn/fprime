**Note:** auto-generated from comments in: ./target/coverage.cmake

## coverage.cmake:

Coverage target adds in gcov endpoint for calculating the coverage of F prime modules. This
coverage requires the system supply a `gcov` target and the code be built with the `TESTING`
build type.  This means the  following things to be setup:

1. `gcov` must be available on the path
2. `-DCMAKE_BUILD_TYPE=TESTING` must be supplied

Once the CMake build directory has been created the user can run the CMake targets
`<MODULE>_coverage` where <MODULE> is the name of the module to generate coverage for. These
_coverage targets perform the following steps:

1. Build and run UT dependencies using the `<MODULE>_check` target
2. Run the `gcov` program on the Module's source files
3. Copy the .gcov reports into a "coverage" subdirectory of the module's source

These targets can be run using the build system as shown in the example below:

**Example**
```
make Svc_CmdDispatcher_Cmd
```
**Note:** although a global `coverage` target is created, it typically should not be used as
CTest provides better global coverage with the `Coverage` target.

## Detailed Function Descriptions

The following functions are used to register the _coverage targets into the target system. They
are required for the system to register custom targets.


##  Function `add_global_target`:

 Adds a global target. Note: only run for "TESTING" builds.

- **TARGET_NAME:** target name to be generated


## Dict function `add_module_target`:

Creates each module's coverage targets.

- **MODULE_NAME:** name of the module
- **TARGET_NAME:** name of target to produce
- **AC_INPUTS:** list of autocoder inputs
- **SOURCE_FILES:** list of source file inputs
- **AC_OUTPUTS:** list of autocoder outputs
- **MOD_DEPS:** hand specified dependencies of target
