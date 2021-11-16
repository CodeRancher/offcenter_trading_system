cmake_minimum_required (VERSION 3.19 FATAL_ERROR)

project (offcenter_trade_system LANGUAGES CXX)

set(BUILD_DOC OFF)

set(OFFCENTER_COMMON_SRC_DIR ".." CACHE STRING "OffCenter Common Source Dir" FORCE)
message(STATUS "OFFCENTER_COMMON_SRC_DIR       ${OFFCENTER_COMMON_SRC_DIR}")
set(OFFCENTER_OANDA_SRC_DIR ".." CACHE STRING "OffCenter Oanda Source Dir" FORCE)
message(STATUS "OFFCENTER_OANDA_SRC_DIR       ${OFFCENTER_OANDA_SRC_DIR}")
set(OFFCENTER_TRADING_SRC_DIR ".." CACHE STRING "OffCenter Trading Source Dir" FORCE)
message(STATUS "OFFCENTER_TRADING_SRC_DIR       ${OFFCENTER_TRADING_SRC_DIR}")
set(OFFCENTER_OTA_SRC_DIR ".." CACHE STRING "OffCenter OTA Source Dir" FORCE)
message(STATUS "OFFCENTER_OTA_SRC_DIR       ${OFFCENTER_OTA_SRC_DIR}")

###############################################################################
# Build combined documentation
option(BUILD_COMBINED_DOC "Build documentation" OFF)
message(STATUS "BUILD_COMBINED_DOC       ${BUILD_COMBINED_DOC}")

###############################################################################
# sub projects
add_subdirectory(offcenter_common)
add_subdirectory(offcenter_oanda)
add_subdirectory(offcenter_trading)

# Only include offcenter_ota if it exists.
# This project is not made available because of patents and proprietary content 
if(IS_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/test")
	add_subdirectory(offcenter_ota)
endif()

add_subdirectory(doc)
