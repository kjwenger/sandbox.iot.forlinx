cmake_minimum_required(VERSION 3.6)
include(Paths)
include(ExternalProject)
ExternalProject_Add(
        cumulocity-agent-linux
        GIT_REPOSITORY https://bitbucket.org/m2m/cumulocity-agents-linux.git
        BUILD_IN_SOURCE 1
        BUILD_COMMAND make release CC=${CMAKE_C_COMPILER} CXX=${CMAKE_CXX_COMPILER} SYSROOT=${CMAKE_PREFIX_PATH}
)
add_dependencies(cumulocity-agent-linux curl)
add_dependencies(cumulocity-agent-linux lua)
add_dependencies(cumulocity-agent-linux cumulocity-sdk-c)
