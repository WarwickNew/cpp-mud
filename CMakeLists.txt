cmake_minimum_required(VERSION 3.0.0)

project(MUD)

# Create vaiables to store all files to be inluded
file(GLOB_RECURSE MUD_SOURCES "src/*.cpp")
file(GLOB_RECURSE MUD_HEADERS "src/*.h")

# Create list of directories that contain headerfiles
set (MUD_INCLUDE_DIRS "")

# Add all header file directories to a list
foreach (_headerFile ${MUD_HEADERS})
	get_filename_component(_dirs ${_headerFile} PATH)
	list (APPEND MUD_INCLUDE_DIRS ${_dirs})
endforeach()
# Remove header file directory duplicates from list
list (REMOVE_DUPLICATES MUD_INCLUDE_DIRS)

# Set C++ standard
set(CMAKE_CXX_STANDARD 11)

# Create executable from sourcefile
add_executable(MUD ${MUD_SOURCES})
# Link headers
target_include_directories(MUD PRIVATE MUD_INCLUDE_DIRS)
