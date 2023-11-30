cmake_minimum_required (VERSION 3.5)

project(subprojects)

# Add sub directories
# wxz 寻找sublibrary1下的CMakeList  这里的CMakeLists需要和sublibrary1同一文件夹下 要不然需要路径
add_subdirectory(sublibrary1)
add_subdirectory(sublibrary2)
add_subdirectory(subbinary)
