cmake_minimum_required(VERSION 3.5)

# Set a default C++ compile flag
# set 命令将 C++ 编译器标志（CMAKE_CXX_FLAGS）的值设置为原始值 ${CMAKE_CXX_FLAGS} 加上一个新的标志 -DEX2。'
# 这表示在原有的编译器标志基础上，添加了 -DEX2 这个预处理器宏定义。
set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -DEX2" CACHE STRING "Set C++ Compiler Flags" FORCE)

# Set the project name
project (compile_flags)

# Add an executable
add_executable(cmake_examples_compile_flags main.cpp)

# 这个命令用于为一个目标（通常是一个库或可执行文件）添加编译定义。
# 编译定义是在编译时传递给预处理器的符号，可以用于控制条件编译或在代码中定义一些常量。
target_compile_definitions(cmake_examples_compile_flags 
    PRIVATE EX3
)


# target_compile_definitions 是 CMake 中用于为目标添加编译定义的命令。它的基本用法如下：

# target_compile_definitions(target_name
#     PRIVATE definition1
#     [PUBLIC definition2]
#     [INTERFACE definition3]
# )

# 其中：

# target_name 是你项目中的目标名称，可以是一个库或可执行文件的名称。

# PRIVATE, PUBLIC, INTERFACE 是定义的作用域。它们用于指定编译定义的可见性。

# definition1, definition2, definition3 是要添加的编译定义。它们通常是预处理器宏，可以在源代码中使用条件编译来检查是否定义了这些宏。

# 具体来说，这些作用域的含义是：

# PRIVATE: 定义仅在目标自身可见，不会传递给依赖该目标的其他目标。

# PUBLIC: 定义既在目标自身可见，也会传递给依赖该目标的其他目标。

# INTERFACE: 定义仅在依赖该目标的其他目标可见，目标自身不可见。