cmake_minimum_required(VERSION 3.0)
project(everything)

enable_testing()

add_subdirectory(testtools)

add_subdirectory(common)

add_subdirectory(iothub_client)
add_subdirectory(serializer)