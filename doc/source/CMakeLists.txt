configure_file(conf.py.in conf.py @ONLY)
configure_file(index.rst.in index.rst @ONLY)

set(RST_FILES motivation.rst
              users_guide.rst
              design.rst)

foreach(RST_FILE ${RST_FILES})
    configure_file(${RST_FILE} ${RST_FILE} COPYONLY)
endforeach()

add_subdirectory(_static)
add_subdirectory(_templates)
add_subdirectory(images)