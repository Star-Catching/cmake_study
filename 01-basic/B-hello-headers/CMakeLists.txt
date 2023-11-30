cmake_minimum_required(VERSION 3.5)
project (hello_headers)

# 创建一个指代源文件的变量，引用更方便 
set(SOURCES
    src/Hello.cpp
    src/main.cpp
)
add_executable(hello_headers ${SOURCES}) # 前面set把 src/Hello.cpp  src/main.cpp 赋值给SOURCES 这里就写${SOURCES}


# 只会为指定目标包含头文件搜索路径， 不放这句make会报错找不到头文件  （要不就在cpp文件里把所有头文件的路径补全）  可以注释掉执行看一下
# 这里hello_headers为指定文件


# target_include_directories(test  xxx  ${PROJECT_SOURCE_DIR}/include)**
# 如果xxx为**PRIVATE**   则表示头文件只能由 test使用
# 如果xxx为**INTERFACE**   则表示头文件只能由 调用test的文件使用
# 如果xxx为**PUBLIC**  则test和任何调用test的文件都能使用头文件

target_include_directories(hello_headers
    PRIVATE
        /home/wxz/C++敲代码/cmake_study/01-basic/B-hello-headers/include
)