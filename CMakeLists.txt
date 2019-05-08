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

     include_directories(octomap/include)

     fips_files(
        octomap/octomap/src/math/Pose6D.cpp
        octomap/octomap/src/math/Quaternion.cpp
        octomap/octomap/src/math/Vector3.cpp          
        octomap/octomap/src/AbstractOcTree.cpp
        octomap/octomap/src/AbstractOccupancyOcTree.cpp
        octomap/octomap/src/Pointcloud.cpp
        octomap/octomap/src/ScanGraph.cpp
        octomap/octomap/src/CountingOcTree.cpp
        octomap/octomap/src/OcTree.cpp
        octomap/octomap/src/OcTreeNode.cpp
        octomap/octomap/src/OcTreeStamped.cpp
        octomap/octomap/src/ColorOcTree.cpp
      ) 


    fips_end_lib()


endif()

if (NOT FIPS_IMPORT)
    fips_finish()
endif()