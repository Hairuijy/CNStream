set(module_name core)
include_directories(${PROJECT_SOURCE_DIR}/modules/${module_name}/include)
if(NOT cnstream_build_integrated_lib)
  file(GLOB srcs ${PROJECT_SOURCE_DIR}/modules/${module_name}/src/*.cpp)
  add_library(cnstream SHARED ${srcs})
  target_link_libraries(cnstream cnstream-toolkit cnrt)
  set_target_properties(cnstream PROPERTIES VERSION ${CNSTREAM_TARGET_VERSION} SOVERSION ${CNSTREAM_TARGET_SOVERSION})
endif()
