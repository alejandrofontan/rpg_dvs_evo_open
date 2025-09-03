project(vikit_ros)
cmake_minimum_required(VERSION 2.8.3)

find_package(catkin_simple REQUIRED)
catkin_simple()

find_package(glog REQUIRED)

include(SvoSetup)

set(HEADERS
  include/vikit/img_type_conversion.h
  include/vikit/output_helper.h
  include/vikit/params_helper.h
  )

set(SOURCES
  src/output_helper.cpp
  src/img_type_conversion.cpp
  )

# Create vikit library
cs_add_library(${PROJECT_NAME} ${SOURCES} ${HEADERS})
target_link_libraries(${PROJECT_NAME}
  ${catkin_LIBRARIES}
  glog::glog
)

################################################################################
cs_install()
cs_export(INCLUDE_DIRS ${glog_INCLUDE_DIRS})

