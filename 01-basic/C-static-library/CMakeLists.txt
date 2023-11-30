cmake_minimum_required(VERSION 3.5)

project(hello_library)

# add_library(生成的库名称  STATIC/SHARED  源文件.cpp):将源文件生成 静态/共享 库文件
# 这里是把hello.cpp 打包成 静态hello_library库
# 这将用于创建名为 libhello _ library. a 的静态库（不明白为什么是这个名，反正生成的二进制文件叫这个名字，后面cmake代码使用的还是hello_library这个名字）
add_library(hello_library STATIC 
    src/Hello.cpp
)

target_include_directories(hello_library
    PUBLIC 
        ${PROJECT_SOURCE_DIR}/include )  # ${PROJECT_SOURCE_DIR} 用于构建源代码目录的路径以便在后续的 CMake 指令中使用。这样做的好处是，无论你将项目放在何处，CMake 都能够正确地找到源代码目录，而无需手动更改路径。

add_executable(hello_binary  
    src/main.cpp
)

# target_link_libraries (库/可执行文件    library1 library2 ...) : 为库或者可执行文件添加需要链接的库 
# 注：需要放在add_executable之后
# 前面add_executable 光有一个main.cpp 是编译不了的 缺少hello.cpp  ，所以这里把 add_library将hello.cpp打包成的库文件链接在一起
# 要不然需要在add_executable 后面继续加一个src/Hello.cpp，这里只是演示生成库和链接库的用法，所以把hello.cpp打包成库文件了
target_link_libraries( hello_binary
    PRIVATE 
        hello_library
)
