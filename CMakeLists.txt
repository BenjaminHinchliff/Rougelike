# CMakeList.txt : CMake project for Rougelike, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.8)

project ("Rougelike")

# Add source to this project's executable.
add_executable (Rougelike "Rougelike.cpp")

if(WIN32 OR MVSC)
	add_subdirectory(pdcurses)
	target_link_libraries(Rougelike PRIVATE pdcurses)
else()
	find_package(curses REQUIRED)
	target_link_options(Rougelike PRIVATE curses)
endif()