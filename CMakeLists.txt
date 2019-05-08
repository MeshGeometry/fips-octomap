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
        octomap/src/math/Pose6D.cpp
        octomap/src/math/Quaternion.cpp
        octomap/src/math/Vector3.cpp          
        octomap/src/AbstractOcTree.cpp
        octomap/src/AbstractOccupancyOcTree.cpp
        octomap/src/Pointcloud.cpp
        octomap/src/ScanGraph.cpp
        octomap/src/CountingOcTree.cpp
        octomap/src/OcTree.cpp
        octomap/src/OcTreeNode.cpp
        octomap/src/OcTreeStamped.cpp
        octomap/src/ColorOcTree.cpp
      ) 


    fips_end_lib()


endif()

if (NOT FIPS_IMPORT)
    fips_finish()
endif()