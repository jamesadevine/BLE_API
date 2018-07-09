project(ble)

include("${CODAL_UTILS_LOCATION}")

# find sources and headers
RECURSIVE_FIND_DIR(TOP_LEVEL_INCLUDE_DIRS "${CMAKE_CURRENT_SOURCE_DIR}/ble" "*.h")
RECURSIVE_FIND_FILE(TOP_LEVEL_SOURCE_FILES "${CMAKE_CURRENT_SOURCE_DIR}/source" "*.c??")

# add them
MESSAGE("aaa ${CMAKE_CURRENT_SOURCE_DIR}")
SET(BASEPATH "${CMAKE_CURRENT_SOURCE_DIR}")
include_directories(${BASEPATH} ${TOP_LEVEL_INCLUDE_DIRS})

# create our target
add_library(ble ${TOP_LEVEL_SOURCE_FILES})

target_link_libraries(
    ble
    mbed-classic
)

# expose it to parent cmake.
target_include_directories(ble PUBLIC ${BASEPATH} ${TOP_LEVEL_INCLUDE_DIRS})