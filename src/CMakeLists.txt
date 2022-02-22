cmake_minimum_required(VERSION 3.9 FATAL_ERROR)

project(my_project CXX C)

add_executable(my_project
	./setup_services.hpp
	./setup_services.cpp

	./screens/test_screen.hpp
	./screens/test_screen.cpp

	./main.cpp
)

target_link_libraries(my_project PUBLIC
	imgui_service
	screen_director

	opengl_renderer_s
	imgui_render_task

	#sound_service
	filesystem_soloud_file

	imgui_tools
	imgui_sound
	imgui_opengl_renderer_tools

	organizer_scene

	#random

	transform_system
)

if(EMSCRIPTEN)
	target_link_libraries(my_project
		PUBLIC
			-sMIN_WEBGL_VERSION=2
			-sALLOW_MEMORY_GROWTH=1
			#"--preload-file ${CMAKE_CURRENT_SOURCE_DIR}/../res@/"
	)
endif()

