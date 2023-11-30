cmake_minimum_required(VERSION 3.5)

# Set a default build type if none was specified
# if(NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES): 这个条件语句检查变量 CMAKE_BUILD_TYPE 是否为空，
# 并且检查是否存在 CMAKE_CONFIGURATION_TYPES。CMAKE_BUILD_TYPE 用于指定构建类型，
# 例如 "Debug"、"Release" 等。CMAKE_CONFIGURATION_TYPES 是在多配置生成器（例如 Visual Studio）中使用的。

# message("Setting build type to 'RelWithDebInfo' as none was specified."): 
# 如果构建类型为空，会输出一条消息说明将构建类型设置为 'RelWithDebInfo'。

# set(CMAKE_BUILD_TYPE RelWithDebInfo CACHE STRING "Choose the type of build." FORCE): 
# 设置构建类型为 'RelWithDebInfo'，并将其缓存起来。FORCE 标志表示无论用户是否设置构建类型，都会强制将其设置为 'RelWithDebInfo'。

# set_property(CACHE CMAKE_BUILD_TYPE PROPERTY STRINGS "Debug" "Release" "MinSizeRel" "RelWithDebInfo"): 
# 设置 CMAKE_BUILD_TYPE 的可能值，这在使用 cmake-gui 进行配置时会用到。
# 这里定义了四种可能的构建类型："Debug"、"Release"、"MinSizeRel" 和 "RelWithDebInfo"。
if(NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
  message("Setting build type to 'RelWithDebInfo' as none was specified.")
  set(CMAKE_BUILD_TYPE RelWithDebInfo CACHE STRING "Choose the type of build." FORCE)
  # Set the possible values of build type for cmake-gui
  set_property(CACHE CMAKE_BUILD_TYPE PROPERTY STRINGS "Debug" "Release"
    "MinSizeRel" "RelWithDebInfo")
endif()

# Set the project name
project (build_type)

# Add an executable
add_executable(cmake_examples_build_type main.cpp)