cmake_minimum_required(VERSION 3.5)

project(hello_library)

# 将src/Hello.cpp生成共享库hello_library
add_library(hello_library SHARED 
    src/Hello.cpp
)

# 给库文件hello_library起别名为hello::library，后面使用hello_library和hello::library都行
add_library(hello::library ALIAS hello_library)

target_include_directories(hello_library
    PUBLIC 
        ${PROJECT_SOURCE_DIR}/include
)


add_executable(hello_binary
    src/main.cpp
)


target_link_libraries( hello_binary
    PRIVATE 
        hello::library
)