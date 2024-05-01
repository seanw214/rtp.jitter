# This CMakeLists.txt file does the following:

# Sets the list of source files (source_file.cpp) and header files 
# (header_file1.h, header_file2.h, header_file3.h).Defines a library
# target named rtp_jitter using add_library. It includes both the
# source and header files. Sets the include directories for the 
# library target to include the current directory, so that the headers
# can be included using #include "header_file.h" from any source file
# that links to this library.


#####


# Add the source files
set(SOURCES
    rtp_jitter.cpp
)

# Add the header files
set(HEADERS
    rtp_jitter.h
    rtp.h
    stdinc.h
)

# Add the executable/library target
add_library(rtp_jitter ${SOURCES} ${HEADERS})

# Set include directories for headers
target_include_directories(rtp_jitter PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})


#####


# Now, in your parent CMake project, you can include this subdirectory 
# using add_subdirectory:

# add_subdirectory(deps/rtp.jitter EXCLUDE_FROM_ALL)

# The EXCLUDE_FROM_ALL option in the add_subdirectory() command is used 
# to exclude the specified subdirectory from being built when you build 
# the parent project with the make or cmake --build command. When you 
# use add_subdirectory() without EXCLUDE_FROM_ALL, CMake includes the 
# specified subdirectory in the build process by default. 

# This means that when you build the parent project, CMake will also build
# the targets defined in the subdirectory. However, when you use add_subdirectory()
# with EXCLUDE_FROM_ALL, CMake still generates build files for the targets
# in the specified subdirectory, but those targets won't be built by default
# when you build the parent project. You would need to explicitly build the
# targets in that subdirectory if you want them to be built. 

# This option is useful when you have auxiliary or optional components in your
# project that you don't want to build every time you build the parent project.
# For example, if you have additional tools, tests, or examples in a subdirectory
# that you only want to build in specific situations, you can use EXCLUDE_FROM_ALL 
# to prevent them from being built by default.
