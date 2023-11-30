cmake_minimum_required(VERSION 3.5)

project(cmake_examples_install)

add_library(cmake_examples_inst SHARED
    src/Hello.cpp
)



target_include_directories(cmake_examples_inst
    PUBLIC 
        ${PROJECT_SOURCE_DIR}/include
)



add_executable(cmake_examples_inst_bin
    src/main.cpp
)


target_link_libraries( cmake_examples_inst_bin
    PRIVATE 
        cmake_examples_inst
)


# 告诉cmake将名为cmake_examples_inst_bin可执行文件安装到目标路径bin
# ${CMAKE_INSTALL_PREFIX}/bin 是默认的安装路径，可以通过 CMAKE_INSTALL_PREFIX 变量进行修改。
# 作用：
#install (TARGETS cmake_examples_inst_bin DESTINATION bin): 安装可执行文件或二进制文件到系统的二进制目录（通常是 /bin）。这样，用户可以直接在命令行中运行该可执行文件。
install (TARGETS cmake_examples_inst_bin
    DESTINATION bin)

# 告诉CMake将名为 cmake_examples_inst 的目标文件（可能是一个共享库）安装到目标路径 lib。
# ${CMAKE_INSTALL_PREFIX}/lib 是默认的安装路径，同样可以通过 CMAKE_INSTALL_PREFIX 变量进行修改。
# 作用：
# install (TARGETS cmake_examples_inst LIBRARY DESTINATION lib): 安装共享库文件到系统的库目录（通常是 /lib 或 /lib64）。其他项目可以链接这个库来使用其中定义的函数和符号。
install (TARGETS cmake_examples_inst
    LIBRARY DESTINATION lib)


# 告诉CMake将源代码目录中的 include 子目录的内容（头文件）安装到目标路径 include。
# ${CMAKE_INSTALL_PREFIX}/include 是默认的安装路径，同样可以通过 CMAKE_INSTALL_PREFIX 变量进行修改。
# 作用：
# install(DIRECTORY ${PROJECT_SOURCE_DIR}/include/ DESTINATION include): 安装头文件到系统的 include 目录。其他项目在编译时可以包含这些头文件来使用你的库的功能。
install(DIRECTORY ${PROJECT_SOURCE_DIR}/include/ 

    DESTINATION include)

# 告诉CMake将名为 cmake-examples.conf 的文件安装到目标路径 etc。
# ${CMAKE_INSTALL_PREFIX}/etc 是默认的安装路径，同样可以通过 CMAKE_INSTALL_PREFIX 变量进行修改。
# 作用：
# install (FILES cmake-examples.conf DESTINATION etc): 安装配置文件到系统的 /etc 目录。配置文件通常包含一些项目的配置信息，其他应用程序或用户可以根据这些信息调整其行为。
install (FILES cmake-examples.conf
    DESTINATION etc)