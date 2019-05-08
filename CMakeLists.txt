set(CMAKE_CXX_STANDARD 17)

if (NOT FIPS_IMPORT)
    cmake_minimum_required(VERSION 2.8)
    get_filename_component(FIPS_ROOT_DIR "../fips" ABSOLUTE)
    include("${FIPS_ROOT_DIR}/cmake/fips.cmake")
    fips_setup()
    fips_project(fips-octomap)
endif()

if ((FIPS_MACOS OR FIPS_WINDOWS OR FIPS_LINUX) AND NOT (FIPS_RASPBERRYPI OR FIPS_OSX_USE_ARC OR FIPS_UWP))

     fips_begin_lib(octomap)

     include_directories(include)

     fips_files(
        src/math/Pose6D.cpp
        src/math/Quaternion.cpp
        src/math/Vector3.cpp          
        src/AbstractOcTree.cpp
        src/AbstractOccupancyOcTree.cpp
        src/Pointcloud.cpp
        src/ScanGraph.cpp
        src/CountingOcTree.cpp
        src/OcTree.cpp
        src/OcTreeNode.cpp
        src/OcTreeStamped.cpp
        src/ColorOcTree.cpp
      ) 


    fips_end_lib()


endif()

if (NOT FIPS_IMPORT)
    fips_finish()
endif()