add_subdirectory(source)

add_custom_command(OUTPUT sphinx_html.stamp
                   COMMAND sphinx-build -bhtml source html
                   COMMAND echo "timestamp" >> sphinx_html.stamp
                   WORKING_DIRECTORY ${PROJECT_BINARY_DIR}/doc)
add_custom_target(html_doc 
                  DEPENDS sphinx_html.stamp)
                  
add_dependencies(html html_doc)
                 