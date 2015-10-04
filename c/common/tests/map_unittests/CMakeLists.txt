#this is CMakeLists.txt for map_unittests
cmake_minimum_required(VERSION 3.2)

set(map_unittests_cpp_files
map_unittests.cpp
)

set(map_unittests_c_files
../../src/map.c
../../src/crt_abstractions.c
)

set(map_unittests_h_files
)

include_directories(${COMMON_SRC_FOLDER} ${MICROMOCK_INC_FOLDER} ${TESTRUNNERSWITCHER_INC_FOLDER} ${CTEST_INC_FOLDER} $ENV{VCInstallDir}UnitTest/include)
link_directories($ENV{VCInstallDir}UnitTest/lib)

IF(WIN32)
	#windows needs this define
	add_definitions(-D_CRT_SECURE_NO_WARNINGS)
	add_definitions(-DCPP_UNITTEST -DGB_MEASURE_MEMORY_FOR_THIS -DGB_DEBUG_ALLOC)
ENDIF(WIN32)


add_library(
map_unittests SHARED ${map_unittests_cpp_files} ${map_unittests_h_files} ${map_unittests_c_files}
)

target_link_libraries(map_unittests micromock ctest)