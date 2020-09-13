project( apriltag2 )

cmake_minimum_required(VERSION 3.4.1)

#set(CMAKE_C_FLAGS "-std=gnu99 -fPIC -Wall -Wno-unused-parameter -Wno-unused-function -I. -O4")

message("CMAKE_SOURCE_DIR=${CMAKE_SOURCE_DIR}")


include_directories(apriltag2 PUBLIC /var/tmp/parent/third_party/del/include)


file(GLOB apriltag2_SRC "src2/*.cpp")
file(GLOB apriltag2_HEADERS "inlude/*.h")

set(APRILTAG2_SRCS ${apriltag2_SRC})
set(APRILTAG2_HEADERS ${apriltag2_HEADERS})

message(STATUS "CMAKE_CURRENT_LIST_DIR=${CMAKE_CURRENT_LIST_DIR}")

add_library(apriltag2 STATIC ${APRILTAG2_SRCS})



project( apriltag1 )

message("CMAKE_SOURCE_DIR=${CMAKE_SOURCE_DIR}")

include_directories(apriltag1 PUBLIC /var/tmp/parent/third_party/del/include)

file(GLOB apriltag1_SRC "src1/*.cpp")
file(GLOB apriltag1_HEADERS "src1*.h")

set(APRILTAG1_SRCS ${apriltag1_SRC})
set(APRILTAG1_HEADERS ${apriltag1_HEADERS})

message(STATUS "CMAKE_CURRENT_LIST_DIR=${CMAKE_CURRENT_LIST_DIR}")

add_library(apriltag1 STATIC ${APRILTAG1_SRCS})




project( apriltag3 )


message("CMAKE_SOURCE_DIR=${CMAKE_SOURCE_DIR}")


include_directories(apriltag3 PUBLIC /var/tmp/parent/third_party/del/include)


file(GLOB apriltag3_SRC "src3/*.cpp")
file(GLOB apriltag3_HEADERS "src3/*.h")

set(APRILTAG3_SRCS ${apriltag3_SRC})
set(APRILTAG3_HEADERS ${apriltag3_HEADERS})

message(STATUS "CMAKE_CURRENT_LIST_DIR=${CMAKE_CURRENT_LIST_DIR}")

add_library(apriltag3 STATIC ${APRILTAG3_SRCS})


add_library(del INTERFACE)
target_link_libraries(del INTERFACE apriltag1 apriltag2 apriltag3)



#project( Tutorial )
#add_executable(Tutorial main.cpp)
#link_libraries(Tutorial PUBLIC apriltag1 apriltag2)



