cmake_minimum_required(VERSION 3.10)

# Don't want to build the tests for this
add_subdirectory(extern/cppzmq)

# Compile the protobuf file and make sure the compiled
# files are accessible. The cpp and h files are both put into
# the binary dir.
find_package(Protobuf REQUIRED)
include_directories(${Protobuf_INCLUDE_DIRS})
include_directories(${CMAKE_CURRENT_BINARY_DIR})
protobuf_generate_cpp(PROTO_SRCS PROTO_HDRS event.proto)

add_executable(main src/main.cpp ${PROTO_SRCS} ${PROTO_HDRS})
target_link_libraries(main cppzmq)
target_link_libraries(main ${Protobuf_LIBRARIES})

add_executable(client src/client.cpp ${PROTO_SRCS} ${PROTO_HDRS})
target_link_libraries(client cppzmq)
target_link_libraries(client ${Protobuf_LIBRARIES})