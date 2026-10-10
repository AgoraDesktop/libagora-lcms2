cmake_minimum_required(VERSION 3.16...3.29)

project(lcms2
  VERSION 2.19
  LANGUAGES C
)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake")

include(Lcms2Options)
include(Lcms2Features)
include(Lcms2Library)
include(Lcms2Tools)
include(Lcms2Plugins)
include(Lcms2Tests)
include(Lcms2Packaging)

lcms2_setup_options()
lcms2_detect_features()

if(LCMS2_BUILD_TESTS)
  enable_testing()
endif()

# AGORA: EVERY LIBRARY IN THIS TREE IS SHARED. A consumer loads the whole .so, so an
# Objective-C category in it is registered whether or not anything references its symbols
# (a static archive drops such members and the categories silently stop answering) and a
# single copy of the runtime state is shared instead of one per binary. See README.md.
option(BUILD_SHARED_LIBS "Build shared libraries" ON)

# AGORA: SHARED ONLY. lcms2 ships a shared and a static target and both switches are ON by default,
# so the static one is turned off here rather than left as an artefact nothing in this tree links.
set(LCMS2_BUILD_SHARED ON)
set(LCMS2_BUILD_STATIC OFF)

lcms2_add_library()

if(LCMS2_BUILD_TOOLS)
  lcms2_add_tools()
endif()

lcms2_add_plugins()

if(LCMS2_BUILD_TESTS)
  lcms2_add_tests()
endif()

lcms2_setup_packaging()


