############################################################################
# <summary> CMakeLists.txt for OpenCV and CUDA. </summary>
# <date>    2012-02-07          </date>
# <author>  Quan Tran Minh. edit by Johannes Kast, Michael Sarahan </author>
# <email>   quantm@unist.ac.kr  kast.jo@googlemail.com msarahan@gmail.com</email>
############################################################################
cmake_minimum_required(VERSION 3.0)
get_filename_component(ProjectId ${CMAKE_CURRENT_SOURCE_DIR} NAME)
project(${ProjectId})
find_package(CUDA)
find_package(OpenCV REQUIRED )

# collect source files

file( GLOB  hdr *.hpp *.h )
file( GLOB  cu  *.cu)
link_directories( ${CMAKE_BINARY_DIR}/bin)
set(HW2_files main.cpp reference_calc.cpp compare.cpp)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)

cuda_add_executable(${CMAKE_PROJECT_NAME} ${HW2_files} ${hdr} ${cu})
target_link_libraries(${CMAKE_PROJECT_NAME} ${OpenCV_LIBS})
