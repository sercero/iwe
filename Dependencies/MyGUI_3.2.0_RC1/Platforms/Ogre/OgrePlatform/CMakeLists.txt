include_directories(
 include
 ${MYGUI_SOURCE_DIR}/MyGUIEngine/include
 ${OGRE_INCLUDE_DIR}
)

include(MyGUI.OgrePlatform.list)

add_library(MyGUI.OgrePlatform ${HEADER_FILES} ${SOURCE_FILES})

add_dependencies(MyGUI.OgrePlatform MyGUIEngine)

target_link_libraries(MyGUI.OgrePlatform ${OGRE_LIBRARIES})
link_directories(${OGRE_LIB_DIR})

install(FILES ${HEADER_FILES}
	DESTINATION include/MYGUI
)
mygui_install_target(MyGUI.OgrePlatform "")

# platform specific dependencies
if (APPLE)
	include_directories(/usr/local/include /usr/include)
	target_link_libraries(${PROJECTNAME} ${Carbon_LIBRARY})
endif ()

# installation rules
install(FILES ${HEADER_FILES}
	DESTINATION include/MYGUI
)
mygui_install_target(MyGUI.OgrePlatform "")
