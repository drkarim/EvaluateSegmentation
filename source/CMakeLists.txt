cmake_minimum_required(VERSION 2.8)
project(EvaluateSegmentation)

find_package(ITK REQUIRED)
include(${ITK_USE_FILE})
if (ITKVtkGlue_LOADED)
  find_package(VTK REQUIRED)
  include(${VTK_USE_FILE})
endif()

add_executable(evalsegment MACOSX_BUNDLE EvaluateSegmentation.cxx)
if( "${ITK_VERSION_MAJOR}" LESS 4 )
  target_link_libraries(evalsegment ITKReview ${ITK_LIBRARIES})
else( "${ITK_VERSION_MAJOR}" LESS 4 )
  target_link_libraries(evalsegment ${ITK_LIBRARIES})
endif( "${ITK_VERSION_MAJOR}" LESS 4 )


if (UNIX)
  INSTALL(TARGETS evalsegment DESTINATION /usr/local/bin)
endif (UNIX)



