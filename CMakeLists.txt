cmake_minimum_required (VERSION 3.8)

# Enable Hot Reload for MSVC compilers if supported.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

set(CMAKE_CXX_STANDARD 17)
project("XXX")

enable_testing()

add_subdirectory(common)
add_subdirectory(package_1)
add_subdirectory(package_2)
add_subdirectory(tests)

find_package(odb CONFIG REQUIRED COMPONENTS sqlite)

# Add source to this project's executable.
add_executable(${PROJECT_NAME} "xxx.cpp" "xxx.h")

# TODO: Add tests and install targets if needed.
target_link_libraries(${PROJECT_NAME} PRIVATE odb::libodb-sqlite)