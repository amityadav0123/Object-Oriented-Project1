cmake_minimum_required( VERSION 3.0 )
set( CMAKE_TOOLCHAIN_FILE "C:/dev/vcpkg/scripts/buildsystems/vcpkg.cmake" )

# Create Project
project( solution )
add_executable( OPENCVTEST main.cpp )

# Set OpenCVConfig.cmake Search Directory
set( OpenCV_DIR )
if( NOT CMAKE_CL_64 )
  set( OpenCV_DIR "" )
else()
  set( OpenCV_DIR "C:\dev\vcpkg\installed\x64-windows\share" )
endif()

# Find Package
find_package( OpenCV REQUIRED )

if( OpenCV_FOUND )
  # Additional Include Directories
  include_directories( ${OpenCV_INCLUDE_DIRS} )

  # Additional Library Directories
  link_directories( ${OpenCV_LIB_DIR} )

  # Additional Dependencies
  target_link_libraries( OPENCVTEST ${OpenCV_LIBS} )
endif()
