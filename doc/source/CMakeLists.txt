configure_file(conf.py.in conf.py @ONLY)
configure_file(index.rst.in index.rst @ONLY)

add_subdirectory(_static)
add_subdirectory(_templates)