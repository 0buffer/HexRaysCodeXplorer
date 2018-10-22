cmake_minimum_required(VERSION 3.1)
project(HexRaysCodeXplorer)

include("ida-cmake/cmake/IDA.cmake")

set(CMAKE_CXX_STANDARD 11)

set(sources "src/HexRaysCodeXplorer/Debug.cpp"
			"src/HexRaysCodeXplorer/CtreeExtractor.cpp"
			"src/HexRaysCodeXplorer/GCCObjectFormatParser.cpp"
			"src/HexRaysCodeXplorer/GCCTypeInfo.cpp"
			"src/HexRaysCodeXplorer/GCCVtableInfo.cpp"
			"src/HexRaysCodeXplorer/IObjectFormatParser.cpp" 
			"src/HexRaysCodeXplorer/MSVCObjectFormatParser.cpp" 
			"src/HexRaysCodeXplorer/ObjectExplorer.cpp" 
			"src/HexRaysCodeXplorer/CodeXplorer.cpp"
			"src/HexRaysCodeXplorer/CtreeGraphBuilder.cpp" 
			"src/HexRaysCodeXplorer/TypeReconstructor.cpp" 
			"src/HexRaysCodeXplorer/TypeExtractor.cpp"
			"src/HexRaysCodeXplorer/Utility.cpp")

if ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "AppleClang")
	# using AppleClang
	set(CMAKE_C_FLAGS "-DUSE_DANGEROUS_FUNCTIONS=1 -DUSE_STANDARD_FILE_FUNCTIONS=1")
	set(CMAKE_CXX_FLAGS "-DUSE_DANGEROUS_FUNCTIONS=1 -DUSE_STANDARD_FILE_FUNCTIONS=1")

elseif("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang")
  # using Clang
  # TODO

elseif ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU")
  	# using GCC
  	# TODO

elseif ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Intel")
  # using Intel C++
  # TODO

elseif ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "MSVC")
  # using Visual Studio C++
  # TODO
endif()

add_ida_plugin(${CMAKE_PROJECT_NAME} ${sources})
