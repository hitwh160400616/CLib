project(ArchClip)

find_package( VTK REQUIRED )
include( ${VTK_USE_FILE} )

# add header files which are generated by qt
include_directories( ${CMAKE_CURRENT_BINARY_DIR} )

file(GLOB UI_FILES *.ui)
file(GLOB HEADER_FILES
    *.h
    *.hpp
    )
file(GLOB CXX_FILES
    *.cxx
    *.cpp
    )

qt5_wrap_ui( UISrcs ${UI_FILES} )
# CMAKE_AUTOMOC in ON so the MOC headers will be automatically wrapped.
set( CMAKE_AUTOMOC ON )
add_executable(${PROJECT_NAME} MACOSX_BUNDLE ${HEADER_FILES} ${CXX_FILES} ${UISrcs} )
qt5_use_modules(${PROJECT_NAME} Core Gui)

target_link_libraries( ${PROJECT_NAME} ${VTK_LIBRARIES} )
