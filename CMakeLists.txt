cmake_minimum_required(VERSION 2.8.9 FATAL_ERROR)
set(CPM_MODULE_NAME boost_graph)

# initialize
if(NOT EXISTS ${CMAKE_CURRENT_BINARY_DIR}/init.cmake)
  file(DOWNLOAD https://raw.github.com/toeb/cpm/master/init-cpm-module.cmake ${CMAKE_CURRENT_BINARY_DIR}/init.cmake)
endif()
include(${CMAKE_CURRENT_BINARY_DIR}/init.cmake)


# All externals *must* define this.
CPM_ForceOnlyOneModuleVersion()


CPM_AddModule("boost_config"
  GIT_REPOSITORY "https://github.com/toeb/cpm-boost-config"
  GIT_TAG "master")

CPM_InitModule(${CPM_MODULE_NAME})

#------------------------------------------------------------------------------
# boost graph library
#------------------------------------------------------------------------------

CPM_EnsureRepoIsCurrent(
    TARGET_DIR "${CMAKE_CURRENT_SOURCE_DIR}/boost/graph"            # Required - Directory in which to place repository.
    GIT_REPOSITORY "https://github.com/boostorg/graph.git"         # Git repository to clone and keep up to date.
    GIT_TAG  boost-1.55.0               # Git tag to checkout.   
    
    )


CPM_ExportAdditionalIncludeDir("${CMAKE_CURRENT_SOURCE_DIR}/boost/graph/include")