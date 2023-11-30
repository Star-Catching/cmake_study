cmake_minimum_required(VERSION 3.5)

project (third_party_include)


# find a boost install with the libraries filesystem and system

# find_package: CMake命令，用于在系统上查找并引入特定的软件包。
# Boost: 要查找的软件包的名称，这里是Boost。
# 1.46.1: 要求的Boost库的版本号，这里是1.46.1。REQUIRED 指定这个版本是必需的，如果找不到指定版本的Boost库，CMake会报错。
# COMPONENTS filesystem system: 指定要查找并引入的Boost库的组件。在这里，它要求引入 filesystem 和 system 两个组件。这将包括Boost库的文件系统和系统相关的功能。
# 一旦 find_package 成功找到并引入了Boost库，接下来你可以使用引入的库进行编译和链接，例如：
# target_link_libraries(your_target_name Boost::filesystem Boost::system)
# wxz 我的理解就是 查找Boost 1.46.1版本的包 ， 用COMPONENTS引入包中的 ilesystem system两个组件
find_package(Boost 1.46.1 REQUIRED COMPONENTS filesystem system)

# check if boost was found
if(Boost_FOUND)
    message ("boost found")
else()
    message (FATAL_ERROR "Cannot find Boost")
endif()

# Add an executable
add_executable(third_party_include main.cpp)

# link against the boost libraries
# wxz 把Boost中的filesystem 链接到third_party_include这个可执行文件里 
target_link_libraries( third_party_include
    PRIVATE
        Boost::filesystem
)
